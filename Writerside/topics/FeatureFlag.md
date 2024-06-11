# FeatureFlag

<b>feature flag是global用于快速开启和关闭某个功能的能力，支持灰度及百分比rollout</b>

### 获取

获取feature flag的retrofit接口及请求参数
```Kotlin
    @Headers(
        "Content-Type: application/vnd.volvocars.api.voc.featurequery.v4+json",
        "Accept: application/vnd.volvocars.api.voc.featurelist.v4+json"
    )
    @POST("/voc/configurations/features")
    suspend fun getFeatureFlags(
        @Body query: QueryParams
    ): FeatureFlagsList
    
@Keep
@Serializable
internal data class QueryParams(
    val client: String? = null,
    val clientVersion: String? = null,
    val uuid: String? = null,
    val userMarket: String? = null,
    val vin: String? = null,
    val vehicleMarket: String? = null,
    val typeCode: String? = null,
    val modelYear: Int? = null,
    val latitude: Double? = null,
    val longitude: Double? = null,
    val telematicsType: String? = null,
    val propulsionType: String? = null,
    val isCodev: Boolean? = null,
)
```
{collapsible="true"}

以下为shell请求示例

```Shell
curl --request POST \
  --url https://gw.consumer.api.volvocars.com/voc/configurations/features \
  --header 'Accept: application/vnd.volvocars.api.voc.featurelist.v4+json' \
  --header 'Content-Type: application/vnd.volvocars.api.voc.featurequery.v4+json' \
  --header 'User-Agent: vca-android/5.37.0' \
  --header 'VCC-Api-Key: 855fec8628e14ba69b0bd8d6a71af78c' \
  --data '{
	"client":"Android",
	"clientVersion":"5.37.0",
	"userMarket":"CN",
	"uuid":"434e75e5e7d52b04fbcad2fefb101bc84067edb52b95d71f60d6fbd682567dde"
}'
```
{collapsible="true"}



```cURL
    curl 'https://gw.consumer.api.volvocars.com/voc/configurations/features'  \
    -H 'Host: gw.consumer.api.volvocars.com'  \
    -H 'Content-Type: application/vnd.volvocars.api.voc.featurequery.v4+json'  \
    -H 'Connection: keep-alive'  \
    -H 'Accept: application/vnd.volvocars.api.voc.featurelist.v4+json'  \
    -H 'VCC-Api-Key: 855fec8628e14ba69b0bd8d6a71af78c'  \
    -H 'Accept-Language: en-US'  \
    -H 'Content-Length: 166'  \
    -H 'Accept-Encoding: gzip, deflate, br'  \
    -H 'User-Agent: Volvo%20Cars/5.35.1.13 CFNetwork/1490.0.4 Darwin/23.2.0'   \
    --data '{
        "clientVersion":"5.35.1",
        "clientEnvironment":"Production",
        "userMarket":"CN",
        "client":"iOS",
        "uuid":"7e9f81563f9b120db2f5c0d69820715ddc09a5d8b64924d5de498809df558b2c"
     }' 
```

```cURL
curl -H 'Host: gw.consumer.api.volvocars.com' -H 'accept: application/vnd.volvocars.api.voc.featurelist.v4+json' -H 'content-type: application/vnd.volvocars.api.voc.featurequery.v4+json' -H 'x-tingyun: c=A|qML6HB1SfvI;u=MDZBRDkyMzEtNDU5MC00MzZCLUJBOTQtODVFNTcyQzE1Qzc4LDU5MTk0NDI=' -H 'vcc-api-key: 855fec8628e14ba69b0bd8d6a71af78c' -H 'user-agent: Volvo%20Cars/5.37.0.0 CFNetwork/1331.0.7 Darwin/21.4.0' -H 'accept-language: en-US' --data-binary '{"clientVersion":"5.37.0.0","client":"iOS","clientEnvironment":"chinaUAT"}' --compressed 'https://gw.consumer.api.volvocars.com/voc/configurations/features'
```

以下为返回的json
```json
[
	{
		"id": "SupportsNewStatistics",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "SupportsRechargeClaimForm",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "SupportsIcupScheduledTimerStatus",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "BatteryChargeTimerCache",
		"product": "Recharge",
		"custom": {
			"cacheLevel": 1,
			"timeToLive": 86400
		}
	},
	{
		"id": "SupportsContactVolvo",
		"product": "Onboarding",
		"custom": {
			"cbvContactEnabled": "true"
		}
	},
	{
		"id": "SupportArticleFeedback",
		"product": "Onboarding"
	},
	{
		"id": "SupportArticlesBrowsing",
		"product": "Onboarding",
		"custom": {}
	},
	{
		"id": "SupportsClassicWLC",
		"product": "Onboarding"
	},
	{
		"id": "SupportsFetchingAllTrips",
		"product": "DriveX"
	},
	{
		"id": "TestNewRules",
		"product": "Core"
	},
	{
		"id": "SupportsAuthEncryptedPrefsMigration",
		"product": "Core"
	},
	{
		"id": "SupportsUserProfileFetchOptimisation",
		"product": "Core",
		"custom": {}
	},
	{
		"id": "SupportsProfileTabParchView",
		"product": "Account"
	},
	{
		"id": "SupportsCbvTermsInLegalView",
		"product": "Account"
	},
	{
		"id": "ChinaForceShowDebugViewInRelease",
		"product": "China"
	},
	{
		"id": "SupportsDriverScore",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "ICupPairingV2",
		"product": "Onboarding"
	},
	{
		"id": "SupportsC3EndOwnership",
		"product": "Onboarding"
	},
	{
		"id": "SupportsEncryptedSharedPreferences",
		"product": "Core",
		"custom": {}
	},
	{
		"id": "SupportsSelectiveVehicleLoading",
		"product": "Core"
	},
	{
		"id": "VccPushSettingsEnabled",
		"product": "EngagementChannel"
	},
	{
		"id": "supportsCarAssetsGraphQL",
		"product": "UiFoundations"
	},
	{
		"id": "EditAccountProfile",
		"product": "Account"
	},
	{
		"id": "SupportsUserConsentApiCepinet",
		"product": "Account"
	},
	{
		"id": "SupportsC3Fuel",
		"product": "C3"
	},
	{
		"id": "SupportsForceStatusUpdateFromVehicle",
		"product": "Ownership",
		"custom": {}
	},
	{
		"id": "ParkingClimatizationStatusCache",
		"product": "Climatization",
		"custom": {
			"cacheLevel": 1,
			"timeToLive": 21600
		}
	},
	{
		"id": "SupportsChargeDetails",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "SupportsScheduledTimerStatus",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "UnpairingWithoutPIN",
		"product": "Onboarding",
		"custom": {}
	},
	{
		"id": "CarManualSearchFromCarStatus",
		"product": "Onboarding"
	},
	{
		"id": "ChinaVersion",
		"product": "Core",
		"custom": {
			"version": "5.20.0",
			"minSdk": 21,
			"storeUrl": "https://www.volvocars.com/zh-cn/v/volvo-cars-app"
		}
	},
	{
		"id": "OpenID",
		"product": "Core",
		"custom": {
			"enabled": true,
			"shouldUseWebFlow": false
		}
	},
	{
		"id": "iCupShownAsBeta",
		"product": "Core"
	},
	{
		"id": "SupportsParseUserFromCFSProfileFirst",
		"product": "Core"
	},
	{
		"id": "SupportsGRPCCarInUseState",
		"product": "Core"
	},
	{
		"id": "supportsCasGraphQLCache",
		"product": "UiFoundations",
		"custom": {
			"timeToLiveInSeconds": 86400
		}
	},
	{
		"id": "BEVersion",
		"product": "CarSharing",
		"custom": {
			"version": "24",
			"qaVersion": "24",
			"testVersion": "1",
			"minIosversion": "10",
			"apiVersion": "0.03",
			"minClientVersion": "0.1",
			"maxClientVersion": "0.2"
		}
	},
	{
		"id": "SupportsOwnerBookingCreation",
		"product": "CarSharing",
		"custom": {}
	},
	{
		"id": "SupportsKoreaConsents",
		"product": "Account"
	},
	{
		"id": "SupportsSubscriptionsListPARCH",
		"product": "Ownership",
		"custom": {}
	},
	{
		"id": "SupportsDisableChargeTimerForPhev",
		"product": "Recharge"
	},
	{
		"id": "supportsForceUX5",
		"product": "Core"
	},
	{
		"id": "SupportsSignInParchView",
		"product": "Core"
	},
	{
		"id": "SupportsCnepmobV1",
		"product": "Core"
	},
	{
		"id": "PushHandlingLibrary",
		"product": "EngagementChannel"
	},
	{
		"id": "testfeature",
		"product": "Labs"
	},
	{
		"id": "SupportsC3Battery",
		"product": "C3"
	},
	{
		"id": "SupportsSharingDriverJournal",
		"product": "Ownership",
		"custom": {}
	},
	{
		"id": "SupportsNewIcupScheduleTimer",
		"product": "MobxHomeElectrification",
		"custom": {}
	},
	{
		"id": "BatteryChargeStatusCache",
		"product": "Recharge",
		"custom": {
			"cacheLevel": 1,
			"timeToLive": 843
		}
	},
	{
		"id": "SupportsVocmoEstimatedRange",
		"product": "Recharge"
	},
	{
		"id": "ShowOrderTrackingEstimatedDeliveryDate",
		"product": "Onboarding"
	},
	{
		"id": "SupportsClassicC3",
		"product": "Onboarding"
	},
	{
		"id": "SupportsTripsFilterScreen",
		"product": "DriveX"
	},
	{
		"id": "TermsAndConditions",
		"product": "Core",
		"custom": {
			"ChangeDate": "2018-01-01T00:00:00"
		}
	},
	{
		"id": "SupportsAuthenticationUseCases",
		"product": "Core"
	},
	{
		"id": "SupportsAppSettingsParchView",
		"product": "Core"
	},
	{
		"id": "SupportsC3Analytics",
		"product": "Core"
	},
	{
		"id": "ChinaAnimationEm",
		"product": "Core"
	},
	{
		"id": "SupportsC3DataSharing",
		"product": "C3"
	},
	{
		"id": "SupportsC3Odometer",
		"product": "C3"
	},
	{
		"id": "SupportsBrazilVocRenewalUrl",
		"product": "Ownership",
		"custom": {}
	},
	{
		"id": "SupportsClimatizationTimers",
		"product": "Climatization"
	},
	{
		"id": "SupportsTspChargingStatus",
		"product": "Recharge"
	},
	{
		"id": "SupportsUX5PromoCard",
		"product": "Core"
	},
	{
		"id": "SupportsMFA",
		"product": "Core"
	},
	{
		"id": "SupportsC3CarAvailability",
		"product": "Core"
	},
	{
		"id": "ChinaVolvoIdcn2ComCN",
		"product": "Core"
	},
	{
		"id": "SupportsFirebaseCrashlytics",
		"product": "Core"
	},
	{
		"id": "SupportsXDaysBooking",
		"product": "CarSharing",
		"custom": {
			"maxBookingDays": "60"
		}
	},
	{
		"id": "SupportsEditPrivacySettingsParchView",
		"product": "Account"
	},
	{
		"id": "SupportsEcommerceTracking",
		"product": "Ownership"
	},
	{
		"id": "SupportsVocEX30CroppedCarTopView",
		"product": "China"
	},
	{
		"id": "SupportsHuaweiCloud",
		"product": "China"
	},
	{
		"id": "SupportsParchChargeTimer",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "SupportsGoogleMapsCompose",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "SupportsIcupC3",
		"product": "Onboarding"
	},
	{
		"id": "iCupPairingRequiresSoftwareUpdate",
		"product": "Core",
		"custom": {
			"reason": "softwareUpdateUnavailable"
		}
	},
	{
		"id": "SupportsCnepmobUrlDiscovery",
		"product": "Core"
	},
	{
		"id": "ChinaSwiftUIControl",
		"product": "Core",
		"custom": {
			"ChinaShowMomentsList": true,
			"ChinaShowActivityList": true,
			"ChinaShowCityList": false
		}
	},
	{
		"id": "NotificationCenter",
		"product": "EngagementChannel"
	},
	{
		"id": "SupportsPrivacySettingsParchView",
		"product": "Account"
	},
	{
		"id": "SupportsUpdatedTermsParchView",
		"product": "Account"
	},
	{
		"id": "SupportsDashboardStatistics",
		"product": "DashboardStatistics"
	},
	{
		"id": "ShowEstimatedPrice",
		"product": "ServiceBooking"
	},
	{
		"id": "CarManualSearchFromCarStatusWarning",
		"product": "Onboarding",
		"custom": {}
	},
	{
		"id": "SupportsIcupVocmo",
		"product": "Onboarding"
	},
	{
		"id": "SupportsNewHomeTab",
		"product": "Onboarding"
	},
	{
		"id": "SupportsObservabilityTracking",
		"product": "Core",
		"custom": {
			"apikey": "eU1yUEVJd0JtMGk2Wnl1am1aQXE6RV91UUNLSlFRb3lqWEMxbGRLSjJnZw==",
			"endpoint": "https://digital-prod.apm.westeurope.azure.elastic-cloud.com",
			"samplingrate": 0.1,
			"servicename": "volvo-cars-app-android"
		}
	},
	{
		"id": "NotificationCenterParch",
		"product": "EngagementChannel"
	},
	{
		"id": "DisableBLEConnection",
		"product": "Vocmo"
	},
	{
		"id": "SupportsSubscriptionTerms",
		"product": "Account"
	},
	{
		"id": "CarSoftwareReleaseNotes",
		"product": "CarCommunications"
	},
	{
		"id": "SupportsNewTspChargeReminder",
		"product": "MobxHomeElectrification",
		"custom": {}
	},
	{
		"id": "SupportsChargingStatus",
		"product": "Recharge"
	},
	{
		"id": "SupportsDataSharingFromCloud",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "PrePairingDesignV2",
		"product": "Onboarding"
	},
	{
		"id": "CarManualSearchFromCarTab",
		"product": "Onboarding"
	},
	{
		"id": "SupportsIcupC3IncompletePairing",
		"product": "Onboarding"
	},
	{
		"id": "SupportsHuanfuC3",
		"product": "Onboarding"
	},
	{
		"id": "SupportsEX30AppRedirect",
		"product": "Onboarding"
	},
	{
		"id": "SupportsOTAInstallationStatus",
		"product": "Core"
	},
	{
		"id": "DisableRevertToUX4",
		"product": "Core"
	},
	{
		"id": "SupportsGeneralPrivacyNotice",
		"product": "Account"
	},
	{
		"id": "SupportsCarDetailsView",
		"product": "Team Aquila",
		"custom": {
			"showVin": true,
			"showRegistrationPlate": true,
			"showWeight": true
		}
	},
	{
		"id": "ParkingClimatizationTimersCache",
		"product": "Climatization",
		"custom": {
			"cacheLevel": 1,
			"timeToLive": 21600
		}
	},
	{
		"id": "EngineRemoteStartStatusCache",
		"product": "Climatization",
		"custom": {
			"cacheLevel": 1,
			"timeToLive": 3600
		}
	},
	{
		"id": "SkipServiceProgram",
		"product": "ServiceBooking",
		"custom": {
			"show_mileage_label": false
		}
	},
	{
		"id": "SupportsBatteryChargeTimer",
		"product": "Recharge",
		"custom": {}
	},
	{
		"id": "GuidesInPrePairing",
		"product": "Onboarding"
	},
	{
		"id": "SupportsC3VINValidation",
		"product": "Onboarding"
	},
	{
		"id": "SupportsEditScreenForDrivingJournal",
		"product": "DriveX"
	},
	{
		"id": "iCup",
		"product": "Core"
	},
	{
		"id": "ChinaWhiteCookies",
		"product": "Core"
	},
	{
		"id": "SupportsPermissions",
		"product": "EngagementChannel"
	}
]
```
{collapsible="true"}



#### 存储
Feature Flag 需要存储在本地，每次启动的时候从服务器异步获取最新的feature flag，然后存储在本地，以便后续使用


#### 使用
```Kotlin
    private suspend fun onFeatureFlagSupportedCloud(featureFlag: String) =
        featuresFlags().map { it.any { cachedFlag -> featureFlag == cachedFlag.id } }
```
{collapsible="true"}