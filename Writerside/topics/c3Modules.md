# c3Modules
```Kotlin
fun VOCApplication.c3Modules() = listOf(
    cnepmobModule,
    carInformationDataModule,
    tripsC3DataModule,
    invocationServiceModule,
    userManagementServiceModule,
    termsAndConditionsDataModule,
    privacySettingsModule,
    statisticsModule,
    servicesDataModule,
    scopesGrantsDataModule,
    statusServiceModule,
    marketingConsentDataModule,
    dtlInternetModule,
    chronosServiceModule,
    maintenanceModule,
)
```
{collapsed-title="c3Modules.kt" collapsible="true" }

* `cnepmobModule`
  * This module is used to configure the dependencies for the CNEP Mob feature. This feature is necessary for China region.
  and it could move to common module
* ``
  * This module is used to initialize the car information api. This could be moved to common modules. 
* `tripsC3DataModule`
  * This module is used to initialize the drive journal api. This could be moved to common modules.
* `invocationServiceModule`
  * This module is used to initialize the invocation grpc service. From code base, this feature is related to lock/unlock
  and may need to move to common modules.
* `userManagementServiceModule`
    * This module is used to initialize the user management grpc service. From code base, this feature is related to vehicle-relationship.This feature is necessary for China region.
  and it could move to common module
* `termsAndConditionsDataModule`
    * This module is used to initialize the terms and conditions api. Our China's terms and conditions are different from global, We use china IAM to let user agree terms and conditions.
  so this module is not necessary for China region.
* `privacySettingsModule`
    * This module is used to initialize the privacy settings api. From code base, this feature seems to be related to data sharing. This feature is necessary for China region.
    and it could move to common module
* `statisticsModule`
    * This module is used to initialize the statistics grpc api. This feature is necessary for China region.
    and it could move to common module
* `servicesDataModule`
  * This module seems not used in anywhere except unit test. **I'm not sure about this one**.
* `scopesGrantsDataModule`
    * This module seems not used in anywhere except unit test. **I'm not sure about this one** .
* `statusServiceModule`
  * This module seems to obtain vehicle status, such as flue,battery,climate, It's used in China region and could move to common module
* `marketingConsentDataModule`
  * China has its own consent solution. If there is no other compliance requirement, it can move to global only modules.
* `dtlInternetModule`
  * This module seems to get car location, if so, this could move to common module
* `chronosServiceModule`
  * Not sure where this module used. **And i'm not sure about this one**
* `maintenanceModule`
  * **Seems this module is duplicate with statusServiceModule.** And this code is not used in anywhere


|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| `cnepmobModule` | - | - | ✅ |
| `carInformationDataModule` | - | - | ✅ |
| `tripsC3DataModule` | - | - | ✅ |
| `invocationServiceModule` | - | - | ✅ |
| `userManagementServiceModule` | - | - | ✅ |
| `termsAndConditionsDataModule` | - | - | ✅ |
| `privacySettingsModule` | - | - | ✅ |
| `statisticsModule` | - | - | ✅ |
| `servicesDataModule` | - | - | - |
| `scopesGrantsDataModule` | - | - | - |
| `statusServiceModule` | - | - | ✅ |
| `marketingConsentDataModule` | ✅ | - | - |
| `dtlInternetModule` | - | - | ✅ |
| `chronosServiceModule` | - | - | - |
| `maintenanceModule` | - | - | ✅ |
