# koinModules09
```Kotlin
fun koinModules09() =
    appCommunicationUIModules +
        SupportUI.koinModules +
        RemoteFunctionsDomainModule.koinModules +
        listOf(
            permissionsDataModule,
            permissionsViewModule,
            permissionsJavaWrapperModule,
            migrationsModule,
            migrationsDataModule,
            migrationsDomainModule {
                register<UnitSettingsMigration>()
            },
            weatherDataModule,
            c3LifecycleDataModule,
            supportDataModule,
            supportDomainModule,
            iterablePushNotificationModule,
            legacyExteriorModule,
            legacyStatisticsModule,
            legacyServiceAndWarningsModule,
            legacyCarCoordinateModule,
        ) +
        appUpdateViewModules
```

* `appCommunicationUIModules`
  * This module seems to be related to the communication between the app and the user. This module is used in the `appCommunicationApiModule` and `appCommunicationDataModule`.
* `SupportUI.koinModules`
  * This modules seems to be related to the volvo manual. This module is used in China Region. It can be moved to common modules.
* `RemoteFunctionsDomainModule.koinModules`
  * This module seems to create a countdown function. This is used for air-purification feature and remote engine function. This can be moved to common modules.**Also, i don't think use clock to implement a countdown function is a good idea.**
* `permissionsDataModule`,`permissionsViewModule`, `permissionsJavaWrapperModule`
  * This module seems to be related to require the permissions. These modules are used in China region. Need to move to common modules.
* `migrationsModule`, `migrationsDataModule`, `migrationsDomainModule`
  * These modules seems to be migrate the settings to datastore. This is used in China region. Need to move to common modules.
* `weatherDataModule`
  * This module seems to be related to the weather data.  This is used in China region. Need to move to common modules.(AQI)
* `c3LifecycleDataModule`
  * This module seems to be related to the all c3 supported remote function. This is used in China region. Need to move to common modules.
* `supportDataModule`, `supportDomainModule`
  * Looks like these modules are a composable webview to load some html. Not sure if they are related to Volvo manual.
* `iterablePushNotificationModule`
  * I don't find any usage in the code base.
* `legacyExteriorModule`
* `legacyStatisticsModule`
* `legacyServiceAndWarningsModule`
* `legacyCarCoordinateModule`
  * Looks like this is the legacy statistic related. China need these modules and need to move to the common module
* `appUpdateViewModules`
  * This modules are related to the global force update and recommend update. China has it's own solution. So it can move to global only modules.


### Conclusion
|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| appCommunicationUIModules | - | - | ✅ |
| SupportUI.koinModules | - | - | ✅ |
| RemoteFunctionsDomainModule.koinModules | - | - | ✅ |
| permissionsDataModule | - | - | ✅ |
| permissionsViewModule | - | - | ✅ |
| permissionsJavaWrapperModule | - | - | ✅ |
| migrationsModule | - | - | ✅ |
| migrationsDataModule | - | - | ✅ |
| migrationsDomainModule | - | - | ✅ |
| weatherDataModule | - | - | ✅ |
| c3LifecycleDataModule | - | - | ✅ |
| supportDataModule | - | - | ✅ |
| supportDomainModule | - | - | ✅ |
| iterablePushNotificationModule | - | - | ✅ |
| legacyExteriorModule | - | - | ✅ |
| legacyStatisticsModule | - | - | ✅ |
| legacyServiceAndWarningsModule | - | - | ✅ |
| legacyCarCoordinateModule | - | - | ✅ |
| appUpdateViewModules | ✅ | - | - |