# debugToolsModules

```Kotlin
object DebugToolsModule {
    val koinModules =
        debugToolsModules +
            featureFlagsModules +
            publicChargingModules +
            insuranceModules
}

private val debugToolsModules = listOf(
    debugToolsNavigationModule,
    debugToolsActivityModule,
    debugToolsViewModule,
)

private val featureFlagsModules = listOf(
    debugToolsFeatureFlagsDataModule,
    debugToolsFeatureFlagsDomainModule,
    debugToolsFeatureFlagsViewModule,
    debugToolsFeatureFlagsConfigurationModule
)

private val publicChargingModules = listOf(
    debugToolsDanaosAuthCredentialsViewModule
)

private val insuranceModules = listOf(
    debugToolsInsuranceViewModule,
)
```
{collapsible="true" collapsed-title="DebugToolsModule.kt"} 


## Conclusion
I believe that the debug tools module is a common module. 
It is used to initialize the debug tools feature. This module is used to configure the dependencies for the debug tools feature. This feature is necessary for debugging and testing purposes. 
This module could be moved to a common module.
