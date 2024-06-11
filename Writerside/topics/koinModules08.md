# koinModules08
```Kotlin
fun koinModules08() =
    batteryChargeStatusModule +
    carInformationModule +
    airPurificationModules +
    AirPurificationUI.koinModules +
    AirPurificationDomain.koinModules +
    AirPurificationData.koinModules +
    DrivingJournalModule.koinModules +
    supportedFunctionsModule +
    dsbDrivenNavigationModule +
    regionRepositoryModule +
    CarHome.koinModules +
    accountLinkingInstructionViewModule +
    HomeChargingData.koinModules +
    HomeChargingUI.koinModules +
    contentOperationsAnalyticsKoinModule +
    inAppFeedbackPrivacyPolicyViewModule +
    engineRemoteStartStatusModule +
    analyticsDataModule +
    analyticsDomainModule +
    analyticsPrivacyFilterModule +
    BuildInfo.dataModule(
        buildConfigType = BuildConfig.BUILD_TYPE,
        versionName = BuildConfig.VERSION_NAME,
        versionCode = BuildConfig.VERSION_CODE,
        gitBranch = BuildConfig.GIT_BRANCH,
        flavour = BuildConfig.FLAVOR,
    ) +
    openUrlUseCaseModule +
    unRegisterPushUseCaseModule +
    salesSupportDependencies
```

* `batteryChargeStatusModule`
  * This module is used to provide the battery charge status. This module is necessary for the China region. Need to move to common module
* `carInformationModule`
  * This module is used to provide the car information. This module is necessary for the China region. Need to move to common module
* `airPurificationModules`
* `AirPurificationUI.koinModules`
* `AirPurificationDomain.koinModules`
  * These modules are used to provide air purification function. This module is necessary for the China region. Need to move to common module
* `DrivingJournalModule.koinModules`
  * This module is used to provide the driving journal. This module is necessary for the China region. Need to move to common module
* `supportedFunctionsModule`
  * This module is used to provide the supported functions for iCup vehicle. This module is necessary for the China region. Need to move to common module
* `dsbDrivenNavigationModule`
  * 




