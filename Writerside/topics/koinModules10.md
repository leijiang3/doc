# koinModules10

## Code
```Kotlin
fun koinModules10() =
    DanaosDI.koinModules +
    ChargeModule.koinModules +
    RemoteChargingModule.koinModules +
    LockClimateWidgetModule.koinModules +
    fuelStatusDataModule +
    chargeTimerSettingsLegacyDataModule +
    carRangeDomainModule +
    legacyFuelStatusModule +
    updateCalendarModule +
    c3AnalyticsDataModule +
    c3analyticsDomainModule +
    marketingConsentModules +
    QuickSignIn.dataModule +
    QuickSignIn.uiModule +
    helperModule +
    drivingJournalSettingsViewModule +
    observabilityDataModule +
    SalesSupport.UI.koinModules +
    drivingJournalSettingsDataModule +
    drivingJournalSettingsDomainModule +
    appCommunicationApiModule +
    inboxDataModule +
    inboxViewLegacyModule +
    inboxViewModule +
    appCommunicationDataModule +
    appCommunicationDomainModule +
    appCommunicationRoomModule +
    appRatingModule +
    deviceTokenRegistrationDataModule +
    userAttributesDataModule +
    landingEX30ViewModule +
    landingEX30DomainModule +
    legacyCarInformationModule +
    legacyLockStatusModule +
    WallBoxModule.koinModules +
    InsuranceUI.koinModules +
    InsuranceData.koinModules +
    InsuranceDomain.koinModules +
    carImagesModule +
    deviceInfoDataModule +
    deviceInfoDomainModule +
    PlugAndChargeDI.koinModules +
    maintenanceDataModule +
    maintenanceDomainModule +
    maintenanceViewModule
```
{collapsible="true" collapsed-title="koinModules10.kt"}


## Explanation
* `DanaosDI.koinModules`
  * `danaosWebViewModule`
    * I'm not sure about this Danaos server. But this module is just load a WebView. 
* `ChargeModule.koinModules`
  * `chargeViewModule`
    * This module is used to show the charging view and related to remote function.
    this is the view layer. It's needed in China repo. and should move to common modules.
* `RemoteChargingModule.koinModules`
  * `RemoteChargingUI.koinModules`
    * `chargeStatusViewModule`
      * This module is used to get battery info and charging status. China uses this feature and should move to common modules.
    * `chargeLimitSettingsViewModule`
      * This module is used to set the charging limit. China uses this feature and should move to common modules.
    * `chargeLimitViewModule`
      * This module is used to show the charging limit. China uses this feature and should move to common modules.
  * `RemoteChargingDomain.koinModules`
    * `chargeStatusDomainModule`
      * This module is used to get battery info and charging status. China uses this feature and should move to common modules.
    * `chargeLimitDomainModule`
      * This module is used to get/set the charging limit. China uses this feature and should move to common modules.
  * `RemoteChargingData.koinModules`
    * `chargeStatusDataModule`
      * This module is used to get battery status from gRPC. It should move to common modules.
    * `chargeTimerSettingsDataModule`
      * This module is a data layer of charge. It's used to get/set the charging. It's also contains the remote and local data storage. It should move to common modules.
* `LockClimateWidgetModule.koinModules`
  * `widgetRepositoryModule`
  * `selectCarModule`
  * `lockClimateWidgetModule`
  * `externalBaseModule`
  * `unlockConfirmationModule`
  * `lockWidgetModule`
  * `climateWidgetModule`
  * `widgetDataMapperModule`
  * `parkingClimatizationModule`
  * These modules above is related to the lock and climate feature. China uses this feature and should move to common modules.
* `fuelStatusDataModule`
  * This module is used to get fuel status. It contains legacy  China uses this feature and should move to common modules.
* `chargeTimerSettingsLegacyDataModule`
  * This module is used to get charging limit property by legacy channel. China uses this feature and should move to common modules.
* `carRangeDomainModule`
  * This module is used to get range whether fuel or electric. China uses this feature and should move to common modules.
* `legacyFuelStatusModule`
  * This is legacy get fuel status. China uses this feature and should move to common modules.
* `updateCalendarModule`
  * This module is used to update the calendar. I didn't see any usage in code base. *I'm not sure about this one*
* `c3AnalyticsDataModule`
  * This is just for analytics. China has our own solution. **We should sit together and decide how to architecture this.**
* `c3analyticsDomainModule`
  * This is just for analytics. China has our own solution. **We should sit together and decide how to architecture this.**
* `marketingConsentModules`
  * This modules is not used in China app. In China app, when a user login, IAM will consented for this user. This should move to global only modules.
* `QuickSignIn.dataModule`
* `QuickSignIn.uiModule`
  * China has its own quick sign in feature. This should move to global only modules.
* `helperModule`
  * This is used for provide time format utils, should move to common modules.
* `drivingJournalSettingsViewModule`
  * This module is used to show the driving journal settings. China uses this feature and should move to common modules.
* `observabilityDataModule`
  * This module is used to provide the observability data. China doesn't need this feature and should move to global only modules.
* `SalesSupport.UI.koinModules`
    * `productListViewModule`
    * `productDetailsViewModule`
    * China has its own sales related function, this should move to global only modules.
* `drivingJournalSettingsDataModule`
* `drivingJournalSettingsDomainModule`
  * These two modules are used to provide the driving journal settings. China uses this feature and should move to common modules.
* `appCommunicationApiModule`
* `inboxDataModule`
* `inboxViewLegacyModule`
* `inboxViewModule`
* `appCommunicationDataModule`
* `appCommunicationDomainModule`
* `appCommunicationRoomModule`
  * These modules above is related to the inbox view. China uses this feature and should move to common modules.
* `appRatingModule`
  * This module is used to show the app rating dialog. China doesn't use this feature and should move to global only modules.
* `deviceTokenRegistrationDataModule`
  * Related push token register. China uses this feature and should move to common modules.
* `userAttributesDataModule`
  * I'm not sure about this one. Looks like it is a related subscription function. China has our own subscription feature. This may need to move to global only modules.
* `landingEX30ViewModule`
* `landingEX30DomainModule`
  * I believe China app doesn't need a user to get another app to use ex30 related remote function. @Rui It can move to global only modules.
* `legacyCarInformationModule`
* `legacyLockStatusModule`
* `WallBoxModule.koinModules`
  * `WallBoxUI.koinModules`
    * `wallboxOnboardingViewModule`
    * `wallboxActivationViewModule`
    * `wallboxMainViewModule`
    * `wallboxChargeSettingsViewModule`
    * `wallboxChargeScheduleViewModule`
    * `wallboxChargeAmpLimitViewModule`
    * `wallboxChargingHistoryListViewModule`
    * `wallboxManageOwnershipViewModule`
  * `WallboxData`
    * `wallboxDataModule`
  * These modules above is related wall box feature, China has its own wall box feature. This should move to global only modules.
  **Maybe we can aligh a high level architecture for this feature**
* `InsuranceUI.koinModules`
  * `insuranceDetailsViewModule`
  * `insuranceSelectionViewModule`
  * `mapperModule`
* `InsuranceData.koinModules`
  * `insuranceDataSourceModule`
  * `insuranceRepositoryModule`
  * `insuranceMapperModule`
* `InsuranceDomain.koinModules`
  * `insuranceUseCaseModule`
  * These modules above is about new car insurance. China has its own insurance feature. This should move to global only modules.
* `carImagesModule`
  * This module is used to get car images. China uses this feature and should move to common modules.
* `deviceInfoDataModule`
* `deviceInfoDomainModule`
  * These two modules is used to generate device id for single user.  **China also has this feature. But we can use different implementation**. But now this should move to common modules.
* `PlugAndChargeDI.koinModules`
  * `plugAndChargeIntroViewViewModule`
  * `enterCarPCIDViewModule`
  * `activationInProgressViewModule`
  * Not sure about this feature. Need more investigation. *I'm not sure about this one*
* `maintenanceDataModule`
* `maintenanceDomainModule`
* `maintenanceViewModule`
  * These modules above is related to the maintenance feature. China uses some features related to this feature. So I think this should move to common modules.


## Conclusion
|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| DanaosDI.koinModules | - | - | ✅ |
| ChargeModule.koinModules | - | - | ✅ |
| RemoteChargingModule.koinModules | - | - | ✅ |
| LockClimateWidgetModule.koinModules | - | - | ✅ |
| fuelStatusDataModule | - | - | ✅ |
| chargeTimerSettingsLegacyDataModule | - | - | ✅ |
| carRangeDomainModule | - | - | ✅ |
| legacyFuelStatusModule | - | - | ✅ |
| updateCalendarModule | ✅ | - | - |
| c3AnalyticsDataModule | - | - | ✅ |
| c3analyticsDomainModule | - | - | ✅ |
| marketingConsentModules | ✅ | - | - |
| QuickSignIn.dataModule | ✅ | - | - |
| QuickSignIn.uiModule | ✅ | - | - |
| helperModule | - | - | ✅ |
| drivingJournalSettingsViewModule | - | - | ✅ |
| observabilityDataModule | ✅ | - | - |
| SalesSupport.UI.koinModules | ✅ | - | - |
| drivingJournalSettingsDataModule | - | - | ✅ |
| drivingJournalSettingsDomainModule | - | - | ✅ |
| appCommunicationApiModule | - | - | ✅ |
| inboxDataModule | - | - | ✅ |
| inboxViewLegacyModule | - | - | ✅ |
| inboxViewModule | - | - | ✅ |
| appCommunicationDataModule | - | - | ✅ |
| appCommunicationDomainModule | - | - | ✅ |
| appCommunicationRoomModule | - | - | ✅ |
| appRatingModule | ✅ | - | - |
| deviceTokenRegistrationDataModule | - | - | ✅ |
| userAttributesDataModule | ✅ | - | - |
| landingEX30ViewModule | ✅ | - | - |
| landingEX30DomainModule | ✅ | - | - |
| legacyCarInformationModule | ✅ | - | - |
| legacyLockStatusModule | ✅ | - | - |
| WallBoxModule.koinModules | ✅ | - | - |
| InsuranceUI.koinModules | ✅ | - | - |
| InsuranceData.koinModules | ✅ | - | - |
| InsuranceDomain.koinModules | ✅ | - | - |
| carImagesModule | - | - | ✅ |
| deviceInfoDataModule | - | - | ✅ |
| deviceInfoDomainModule | - | - | ✅ |
| PlugAndChargeDI.koinModules | - | - | - |
| maintenanceDataModule | - | - | ✅ |
| maintenanceDomainModule | - | - | ✅ |