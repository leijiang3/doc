# Android-Charger

## 同步车端的时间到桩端
```Kotlin
  /**
     * 同步车控预约充电时间到家充桩
     */
    private fun syncHomeChargingAppointmentTimeFromVehicle() {
        if (presentable.getFirstInit()) {
            presentable.setFirstInit(false)
            suspendable {
                val carInfo = newbieCarInfoRepository.queryCurrentVOCbindCarInfo()
                val vehicle = carInfo.second
                if (vehicle?.vehicleType == VehicleType.VOCMO &&
                    vehicle.vehicleData.attributes.propulsion == Propulsion.ELECTRIC) {
                    val pileData = chargeZoneUseCase.getPileList().getOrNull()
                    if (pileData?.brandPileList?.size == ONE) {
                        val pile = pileData.brandPileList.firstOrNull()
                        ifNotNull(
                            vehicle.vehicleData.charging
                                .acceptedChargeLocations.firstOrNull()?.delayCharging?.startTime,
                            vehicle.vehicleData.charging
                                .acceptedChargeLocations.firstOrNull()?.delayCharging?.endTime
                        ) { startTime, stopTime ->
                            val startTimeFormat = formatTime(startTime.toInt())
                            val endTimeFormat = formatTime(stopTime.toInt())
                            if (startTimeFormat == pile?.appointmentStartTime &&
                                endTimeFormat == pile.appointmentEndTime
                            ) {
                                return@suspendable
                            }
                            if ((startTimeFormat == endTimeFormat) || pile?.appointmentType != ONE) {
                                return@suspendable
                            }
                            chargeZoneUseCase.chargingAppointment(
                                ChargingAppointmentReqParam(
                                    equipmentId = pile.equipmentId ?: "",
                                    connectorId = pile.connectorId ?: "",
                                    appointmentType = ONE,
                                    startTime = startTimeFormat,
                                    endTime = endTimeFormat,
                                    appointmentStatus = if (pile.appointment) THREE else ONE
                                )
                            )
                        }
                    }
                }
            }
        }
    }
```

## 同步桩端的时间到车端
```Kotlin
/**
     * ICup通过车控SDK预约
     * @param appointmentType 预约类型 1:完整的开始时间和结束时间 2:充满为止
     */
    private suspend fun appointmentWithICup(appointmentType: Int, startTime: String, endTime: String) {
        vehicle?.apply {
            val isBev = vehicleType == VehicleType.VOCMO &&
                    vehicleData.attributes.propulsion == Propulsion.ELECTRIC
            if (isBev) {
                val start = calculateMinutesAfterMidnight(startTime)
                var stop = calculateMinutesAfterMidnight(endTime)
                if (appointmentType == TWO) {
                    vehicleData.charging.timeToFullyCharged?.let {
                        stop = (it - System.currentTimeMillis()).toInt() / ONE_MINUTE + start
                    }
                }
                if (start != stop) {
                    val result = saveBatteryChargeTimerUseCase.invoke(
                        BatteryChargeTimer(startTime = start, stopTime = stop, isActivated = true)
                    )
                    result.onFailure {
                        if (it !is CancellationException) {
                            showScheduleCouldNotBeSetFeedback()
                        }
                    }
                }
            }
        }
    }

    fun calculateMinutesAfterMidnight(timeString: String): Int =
        kotlin.runCatching {
            val dateFormat = SimpleDateFormat(TIME_FORMAT, Locale.getDefault(Locale.Category.FORMAT))
            val midnight = dateFormat.parse(TIME_MIDNIGHT)
            val time = dateFormat.parse(timeString)
            TimeUnit.MILLISECONDS.toMinutes(
                (time?.time ?: ZERO.toLong()) - (midnight?.time ?: ZERO.toLong())
            ).toInt()
        }.getOrElse { ZERO }

    private fun showScheduleCouldNotBeSetFeedback() {
        showRemoteControlFeedbackUseCase(
            VehicleAction(
                type = VehicleActionType.SaveBatteryChargeTimer,
                status = VehicleActionStatus.Fail(VehicleActionFailureType.UnknownError),
            )
        )
    }
internal fun ShowRemoteControlFeedbackUseCase.Factory.build(
    remoteControlFeedbackRepository: RemoteControlFeedbackRepository,
) = ShowRemoteControlFeedbackUseCase { vehicleAction ->
    remoteControlFeedbackRepository.publishFeedback(vehicleAction)
}
```