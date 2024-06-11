# iOS-Charger
## 同步车端的时间到桩端
```Swift
// 获取车控时间
    func getVocChargeTime(_ type: VOCScheduleChargeTimeType = .start) -> String {
        guard let vehicle = self.vocSelectVehicle  else {
            return ""
        }
        
        if vehicle.isIcup, vehicle.vehicleData.propulsion == .electric {
            // 支持车控
            if let chargeTime = vehicle.scheduledChargingTimer(selectedVehicle: vehicle) {
                if type == .start {
                    return chargeTime.formatedStartTimeString()
                } else {
                    return chargeTime.formatedStopTimeString()
                }
            }
        }
        return ""
    }

// 标记是否设置了预约时间
    var isSettingAppointmentTime: Bool {
        var isSetting: Bool = false
        if appointmentType == ChargingAppointmentType.fromStartToEnd.rawValue && !appointmentStartTime.isEmpty && !appointmentEndTime.isEmpty {
            isSetting = true
        } else if appointmentType == ChargingAppointmentType.fromStartToFull.rawValue && !appointmentStartTime.isEmpty {
            isSetting = true
        }
        return isSetting
    }

// 车机端修改预约时间同步到桩端
    func fetchReserveChargingDatas(_ pileModel: ChargingMyHomePileListModel) {
        // 240230 桩端预约时间同步添加限制条件（桩端是否已开启预约充电）
        guard pileModel.appointmentSwitchIsOn else { return }
        
        var appointmentStatus = AppointmentStatusType.appointment.rawValue
        if pileModel.isSettingAppointmentTime {
            appointmentStatus = AppointmentStatusType.updateAppointment.rawValue
        }
        // 车控预约开始时间
        let startTime = getVocChargeTime(.start)
        // 车控预约结束时间
        let endTime = getVocChargeTime(.end)
        
        // 231130 修复 当车机时间一致时不同步
        if startTime == endTime {
            return
        }
        
        // 车机端的预约时间如果跟桩的预约时间一致,则不需要同步至桩端
        if startTime == pileModel.appointmentStartTime && endTime == pileModel.appointmentEndTime {
            return
        }
        // 机车端时间同步至桩端
        var params: [String: Any] = [:]
        params["appointmentStatus"] = appointmentStatus
        params["startTime"] = startTime
        params["endTime"] = endTime
        params["equipmentId"] = pileModel.equipmentId
        params["appointmentType"] = pileModel.myAppointmentType
        params["connectorId"] = pileModel.connectorId
        params["channelType"] = 3
        let api = ChargingMyHomePileAppointmentApi(params: params)
        fetchReserveChargingHomePilePublisher.send(api)
    }

```



## 同步桩端的时间到车端
```Swift
/// 判断开始时间是否与结束时间一致
    func starIsStop() -> Bool {
        guard let pileModel,
              pileModel.appointmentStartTime == pileModel.appointmentEndTime else { return false }
        return true
    }
    
    // 预约/取消/更新预约充电
    func fetchReserveChargingHomePile() {
        var params: [String: Any] = [:]
        params["appointmentStatus"] = self.statusType.rawValue
        params["startTime"] = pileModel?.appointmentStartTime ?? ""
        params["endTime"] = pileModel?.appointmentEndTime ?? ""
        params["equipmentId"] = pileModel?.equipmentId ?? ""
        params["appointmentType"] = pileModel?.myAppointmentType
        params["connectorId"] = pileModel?.connectorId ?? ""
        params["channelType"] = 1
        
        let startT = getTimestampFromTimeStr(pileModel?.appointmentStartTime ?? "")
        let stopT = getTimestampFromTimeStr(pileModel?.appointmentEndTime ?? "")
        // TODO: 5.35 ChargeTimer->BatteryChargeTimer
        let timer = BatteryChargeTimer(start: UInt32(startT),
                                       stop: UInt32(stopT),
                                       activated: true)
        saveSchedule(chargeTimer: timer)
        let api = ChargingMyHomePileAppointmentApi(params: params)
        fetchReserveChargingHomePilePublisher.send(api)
    }
    
    // 计算global所需的时间
    func getTimestampFromTimeStr(_ timeStr: String) -> TimeInterval {
        guard !timeStr.isEmpty else { return 0 }
        let arr = timeStr.components(separatedBy: ":")
        guard let hourStr = arr.first,
              let secondStr = arr.last,
              let hour = TimeInterval(hourStr),
              let second = TimeInterval(secondStr) else { return 0 }
        
        return hour * 60 * 60 + second * 60
    }
    
    func saveSchedule(chargeTimer: BatteryChargeTimer) {
        // TODO: 5.35
        let vocVehicle = AppDelegate.shared.selectedVocVehicle
        let isIcup = vocVehicle?.isIcup
        if let vehicle = vocVehicle as? VocmoVehicleProtocol, isIcup == true {
            vehicle.requestSetBatteryChargeTimer(batteryChargeTimer: chargeTimer) { _ in }
        }
    }
    
    func updateAppointmentStatus(_ status: AppointmentStatusType) {
        self.statusType = status
    }
```