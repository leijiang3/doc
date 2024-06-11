# TspParingFlow

### Step one:InputPin
- 创建人车关系
```Kotlin
    data class VehicleRelationInputDTO(
        @SerializedName("regNo") val regNo: String? = null,
        @SerializedName("vin") val vin: String? = null,
        @SerializedName("pin") val pin: String? = null,
        @SerializedName("ISO2CountryCode") val iSO2CountryCode: String? = null,
    ) : Serializable


    @Headers(
        "Accept: application/vnd.wirelesscar.com.voc.CustomerVehicleRelation.v4+json; charset=utf-8",
        "Content-Type: application/vnd.wirelesscar.com.voc.VehicleRelationInput.v4+json; charset=utf-8"
    )
    @POST("https://vocapi.cn.prod.vocw.cn/customerapi/rest/vehicle-account-relations")
    suspend fun createAccountRelation(@Body vehicleRelationPostDto: VehicleRelationInputDTO): CustomerVehicleRelationDTO
```
- 从返回中取出对应的vehicleAccountRelation.vehicle.vehicle

- 循环获取是否长按车机上的onCall
```Kotlin
/tspVehicles/{vehiclehandle}/connectionStatus
```

