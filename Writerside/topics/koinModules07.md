# koinModules07
```Kotlin
fun koinModules07() =
    PublicCharging.UI.koinModules +
            RemoteCharging.UI.koinModules +
            remoteChargingDomainModule +
            remoteChargingDataModule +
            PaymentData.koinModules +
            MarketsData.koinModules +
            InvoiceDataModules.koinModules +
            SubscriptionsData.koinModules +
            SubscriptionsUI.koinModules +
            PaymentUI.koinModules +
            InvoicesUI.koinModules +
            DrivingJournalUi.koinModules +
            EcarxDrivingJournalUi.koinModules +
            CarGarageUI.koinModules +
            CarSoftware.UI.koinModules +
            OtaData.koinModules +
            listOf(
                mapFilterBottomSheetViewViewModule, mapTypeBottomSheetViewViewModule,
                carLocatorViewModule,
                carLocatorComposeModule,
                carLocatorDomainModule,
                carLocatorDataModule,
                educationalComponentDataModule,
                publicChargingDependencies,
                publicChargingDataModule,
                publicChargingDomainModule,
                unitSystemFormatterModule,
                statisticsModule,
                statisticsSharedModule,
                statisticsDomainModule,
                carAssetsDataModule,
                carExteriorDataModule,
                dataSharingModule,
                carAvailabilityDataModule,
                CoDev.dataModule(BuildConfig.VERSION_NAME),
                CoDev.domainModule,
                CoDev.coDevVehicleModule,
                CoDev.coDevViewKoinModule,
                featureFlagsDataModule,
                environmentSelectionDataModule,
                environmentSelectionViewModuleComposeNavigation,
                environmentSelectionViewModuleLegacyNavigation,
                storeActionModule,
                externalActionModule,
                openLegacySettingsModule,
                appSettingsViewKoinModule,
                calendarSettingsDataModule,
                creditsDataModule,
                creditsViewModule,
                unitSettingsDataModule,
                crossBorderDataModule,
                crossBorderDomainModule,
                carOtaSupportModule,
                chinaEnvironmentSelectionViewModuleLegacyNavigation,
                chinaEnvironmentSelectionViewModuleComposeNavigation,
                chinaEnvironmentSelectionBottomSheetViewModule,
                chinaEnvironmentModule,
            )
```
{collapsed-title="koinModules07" collapsible="true" }

* `PublicCharging.UI.koinModules`
* `RemoteCharging.UI.koinModules`
* `remoteChargingDomainModule`
* `remoteChargingDataModule`
    * These modules are related to public charging. Should move to the global-only module
* `PaymentData.koinModules`
* `PaymentUI.koinModules
    * China has its own payment module. This should move to the global-only module
* `MarketsData.koinModules`
    * This module is not used in China. Should move to global-only module
* `InvoicesUI.koinModules`
* `InvoiceDataModules.koinModules`
    * This module is used to provide the invoice UI. This module is not used in the China region. Need to move to global-only module
* `SubscriptionsData.koinModules`
* `SubscriptionsUI.koinModules`
    * This module is used to provide the subscriptions data. This module is not used in the China region. Need to move to global-only module
* `DrivingJournalUi.koinModules`
    * This module is used to provide the driving journal UI. This module is necessary for the China region. Need to move to common module
* `EcarxDrivingJournalUi.koinModules`
    * This module is used to provide the ecarx driving journal UI. This module is necessary for the China region. Need to move to china-only module
* `CarGarageUI.koinModules`
    * China has its own solution, This can move to global-only module
* `CarSoftware.UI.koinModules`
    * This module contains release note and ota related functions. Should move to common module.
* `OtaData.koinModules`
    * This module is used to provide the ota data. This module is necessary for the China region. Need to move to common module
* `mapFilterBottomSheetViewViewModule`
* `mapTypeBottomSheetViewViewModule`
* `carLocatorViewModule`
* `carLocatorComposeModule`
* `carLocatorDomainModule`
* `carLocatorDataModule`
    * These modules are related to the car locator. This module is necessary for the China region. Need to move to common module
* `educationalComponentDataModule`
    *  I don't know what this module is used for. Need to clarify with the team
* `publicChargingDependencies`
* `publicChargingDataModule`
* `publicChargingDomainModule`
    * These modules are related to public charging. Should move to the global-only module
* `unitSystemFormatterModule`
    * This module is used to provide the unit system formatter. This module is necessary for the China region. Need to move to common module
* `statisticsModule`
* `statisticsSharedModule`
* `statisticsDomainModule`
  * These modules are related to the dashboard. China needs these features. Should move to common modules.
* `carAssetsDataModule`
  * This module is used to provide car images. China needs this feature. Should move to common module.
* `carExteriorDataModule`
  * This module looks like to provide car status info, used in all remote control functions. China needs this feature. Should move to common module.
* `dataSharingModule`
  * This module is used to provide the data sharing status. It's necessary for the China region. Need to move to common module
* `carAvailabilityDataModule`
  * This module is used to get the car availability status. used in remote control functions. China needs this feature. Should move to common module.
* `CoDev.dataModule(BuildConfig.VERSION_NAME)`
* `CoDev.domainModule`
* `CoDev.coDevVehicleModule`
* `CoDev.coDevViewKoinModule`
  * These modules are used to provide the co-dev feature. I'm not sure about these modules. But it seems like they should move to common modules.
* `featureFlagsDataModule`
  * This module is used to provide the feature flags. China needs this feature. Should move to common module.
* `environmentSelectionDataModule`
* `environmentSelectionViewModuleComposeNavigation`
* `environmentSelectionViewModuleLegacyNavigation`
  * These modules are used to provide the environment selection feature. China has its own feature. Should move to global-only module.
* `storeActionModule`
* `externalActionModule`
  * This module is used to provide the store action.Looks like when app cold start, it will handle the intent extras and store it. seems related shortcut functions. Needs move to common module.
* `openLegacySettingsModule`
* `appSettingsViewKoinModule`
* `calendarSettingsDataModule`
* `creditsDataModule`
* `creditsViewModule`
* `unitSettingsDataModule`
  * These modules are used to provide the app settings. China use this feature. Should move to common module.
* `crossBorderDataModule`
* `crossBorderDomainModule`
  * These modules are used to provide the cross-border feature. China needs this feature to transfer global data to China owned feature. Should move to china-only module.
* `carOtaSupportModule`
  * This module is used to provide the car ota support. China needs this feature. Should move to common module.
* `chinaEnvironmentSelectionViewModuleLegacyNavigation`
* `chinaEnvironmentSelectionViewModuleComposeNavigation`
* `chinaEnvironmentSelectionBottomSheetViewModule`
* `chinaEnvironmentModule`
  * These modules are only used in the China region to set environment. Should move to china-only modules




## Conclusion
|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| PublicCharging.UI.koinModules | ✅ | - | - |
| RemoteCharging.UI.koinModules | ✅ | - | - |
| remoteChargingDomainModule | ✅ | - | - |
| remoteChargingDataModule | ✅ | - | - |
| PaymentData.koinModules | ✅ | - | - |
| MarketsData.koinModules | ✅ | - | - |
| InvoiceDataModules.koinModules | ✅ | - | - |
| SubscriptionsData.koinModules | ✅ | - | - |
| SubscriptionsUI.koinModules | ✅ | - | - |
| PaymentUI.koinModules | ✅ | - | - |
| InvoicesUI.koinModules | - | - | ✅ |
| DrivingJournalUi.koinModules | - | - | ✅ |
| EcarxDrivingJournalUi.koinModules | - | ✅ | - |
| CarGarageUI.koinModules | ✅ | - | - |
| CarSoftware.UI.koinModules | - | - | ✅ |
| OtaData.koinModules | - | - | ✅ |
| mapFilterBottomSheetViewViewModule | - | - | ✅ |
| mapTypeBottomSheetViewViewModule | - | - | ✅ |
| carLocatorViewModule | - | - | ✅ |
| carLocatorComposeModule | - | - | ✅ |
| carLocatorDomainModule | - | - | ✅ |
| carLocatorDataModule | - | - | ✅ |
| educationalComponentDataModule | - | - | - |
| publicChargingDependencies | ✅ | - | - |
| publicChargingDataModule | ✅ | - | - |
| publicChargingDomainModule | ✅ | - | - |
| unitSystemFormatterModule | - | - | ✅ |
| statisticsModule | - | - | ✅ |
| statisticsSharedModule | - | - | ✅ |
| statisticsDomainModule | - | - | ✅ |
| carAssetsDataModule | - | - | ✅ |
| carExteriorDataModule | - | - | ✅ |
| dataSharingModule | - | - | ✅ |
| carAvailabilityDataModule |  - | - | ✅ |
| CoDev.dataModule(BuildConfig.VERSION_NAME) | - | - | ✅ |
| CoDev.domainModule | - | - | ✅ |
| CoDev.coDevVehicleModule | - | - | ✅ |
| CoDev.coDevViewKoinModule | - | - | ✅ |
| featureFlagsDataModule | - | - | ✅ |
| environmentSelectionDataModule | - | - | ✅ |
| environmentSelectionViewModuleComposeNavigation | - | - | ✅ |
| environmentSelectionViewModuleLegacyNavigation | - | - | ✅ |
| storeActionModule | - | - | ✅ |
| externalActionModule | - | - | ✅ |
| openLegacySettingsModule | - | - | ✅ |
| appSettingsViewKoinModule | - | - | ✅ |
| calendarSettingsDataModule | - | - | ✅ |
| creditsDataModule | - | - | ✅ |
| creditsViewModule | - | - | ✅ |
| unitSettingsDataModule | - | - | ✅ |
| crossBorderDataModule | - | ✅ | - |
| crossBorderDomainModule | - | ✅ | - |
| carOtaSupportModule | - | - | ✅ |
| chinaEnvironmentSelectionViewModuleLegacyNavigation | - | ✅ | - |
| chinaEnvironmentSelectionViewModuleComposeNavigation | - | ✅ | - |
| chinaEnvironmentSelectionBottomSheetViewModule | - | ✅ | - |
| chinaEnvironmentModule | - | ✅ | - |











