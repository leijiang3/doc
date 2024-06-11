# koinModules01

```Kotlin
    val koinModules = listOf(
        newOrderWelcomeKoinModule,
        loadOrdersKoinModule,
        orderDetailsKoinModule,
        carDetailsKoinModule,
        orderStatusKoinModule,
        orderStatusV2KoinModule,
        orderDetailsV2KoinModule,
        noOrderFoundKoinModule,
        errorStatusKoinModule,
        ordersListKoinModule,
        fullScreenCarouselActivityModule,
        fullScreenCarouselKoinModule
    )
```
{collapsible="true" collapsed-title="koinModules.kt" }

```Kotlin
// CbvSubscriptions
    val koinModules = listOf(
        orderSubscriptionKoinModule,
        subscriptionDetailsKoinModule,
        insuranceCardViewModule,
        paymentDetailsKoinModule,
        cbvDocumentsKoinModule,
        pdfViewerActivityModule,
        pdfViewerKoinModule
    )
```
{collapsible="true" collapsed-title="CbvSubscriptions.koinModules.kt" }

```Kotlin
private fun cbvModules() =
    OrderTracking.koinModules +
    CbvSubscriptions.koinModules +
    listOf(
        cbvContactInformationModule,
        cbvMileageProvider
    )
```
{collapsible="true" collapsed-title="cbvModules.kt" }

```Kotlin
private fun homeTabModules() = listOf(
    climateBottomSheetDialogKoinModule,
    climateEditTimerFragmentKoinModule,
    climateFragmentKoinModule,
    climateMCATTimerFragmentKoinModule,
    climateTabFragmentKoinModule,
    climateTimerFragmentKoinModule,
    homeFragmentKoinModule,
    myCarToolboxViewModule,
    myCarContainerViewModule,
    scheduleChargeGuidanceViewModule,
    scheduleChargeSettingsViewModule,
    iCupScheduleChargeSettingsViewModule,
    recentLocationPickerViewModule,
    chargeRemindersSettingsViewModule,
    OtaComplete.domainModule,
    otaCompleteViewModule,
    securityFragmentKoinModule,
    nonConnectedAppointmentViewModule,
    vehicleDetailViewModule,
    vehicleWarningsViewModule,
)
```
{collapsible="true" collapsed-title="homeTabModules.kt" }

```Kotlin
val rootFragmentsModules =
    homeTabModule +
        carTabModule +
        nonConnectedRootModule +
        orderRootModule +
        rootFragmentModule<MapRootFragment> {} +
        rootFragmentModule<VOCMOMapRootFragment> {} +
        supportTabModule +
        profileTabModule +
        profileTabViewModule +
        profileTabComposeModule +
        mallTabModule +
        saleTabModule +
        communityTabModule
```
{collapsible="true" collapsed-title="rootFragmentsModules.kt" }

```Kotlin
fun koinModules01() = rootFragmentsModules + cbvModules() + homeTabModules()
```

* `OrderTracking.koinModules `
    * this koin module is seemed to provide the dependencies for the OrderTracking feature.
    Our China Region has our own order track feature and didn't use the global one.
* `CbvSubscriptions.koinModules `
    * this koin module is seemed to provide the dependencies for the subscription feature.Most of them are not for China region.
    but, in this koin module, there are some dependencies that are used in China region. like the `pdfViewerActivityModule` and `pdfViewerKoinModule`.
      * need to be clarified with the team to decide whether to move these dependencies to the other common koin modules.
* `cbvContactInformationModule`
  * this module is seemed to provide the dependencies for the contact information feature. seems our China region doesn't use this feature.
* `cbvMileageProvider`
  * this feature is used to provide the vehicle dashboard feature, this could be moved to common modules.
* `homeTabModules`
  * `climateBottomSheetDialogKoinModule`,
  * `climateEditTimerFragmentKoinModule`,
  * `climateFragmentKoinModule`,
  * `climateMCATTimerFragmentKoinModule`,
  * `climateTabFragmentKoinModule`,
  * `climateTimerFragmentKoinModule`,
    * the feature above is about climate control feature, this feature is used in China region. and need to be moved to common modules. Also these modules seems need to group together.
  * `scheduleChargeGuidanceViewModule`,
  * `scheduleChargeSettingsViewModule`,
  * `iCupScheduleChargeSettingsViewModule`,
  * `recentLocationPickerViewModule`,
  * `chargeRemindersSettingsViewModule`,
    * the feature above is about schedule charge feature, this feature is used in China region. and need to be moved to common modules.
  * `OtaComplete.domainModule`,
  * `otaCompleteViewModule`,
    * the feature above is about OTA feature, used for ota update, this feature is used in China region. and need to be moved to common modules.
  * `securityFragmentKoinModule`,
    * the feature above is about security feature, used for lock/unlock,(when the user click lock/unlock, it shows a fragment dialog to authenticate users through biometric recognition)this feature is used in China region. and need to be moved to common modules. 
  * `nonConnectedAppointmentViewModule`,
    * looks like this feature is used for service booking, this feature is not used in China region. and need to be moved to only global modules.
  * `vehicleDetailViewModule`,
    * China has it's own vehicle detail view, this feature is not used in China region. and need to be moved to only global modules.
    (looks like this is only for china flavor in global app? if it is so, it can be removed both in global and china repo)
  * `vehicleWarningsViewModule`,
    * I'm not sure if China has already adopted this feature .But this view is more related to service booking, so I guess we didn’t be using it.
  * `myCarToolboxViewModule`
  * `myCarContainerViewModule`
    * This two modules are used for the toolbox feature, this feature is only used in China region. and need to be moved to China modules. Also this toolbox view should remove in global repo.
  * `homeTabModule`
  * `carTabModule`
    * this modules above are seemed to provide the dependencies for the home tab(car tab) feature. this feature is used in China region. and need to be moved to common modules.
  * `nonConnectedRootModule`
    * china doesn't need this feature, this can move to global only
  * `orderRootModule`
    * China has its own order tracking feature, this can move to global only
  * `rootFragmentModule<MapRootFragment> {}`
  * `rootFragmentModule<VOCMOMapRootFragment> {}`
    * This is used for car locator feature, this feature is used in China region. and need to be moved to Common modules.
  * `supportTabModule`
  * `profileTabModule`
  * `profileTabViewModule`
  * `profileTabComposeModule`
    * these feature above is all for global only , and need to move to global only modules.




|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| climateBottomSheetDialogKoinModule | - | - | ✅ |
| climateEditTimerFragmentKoinModule | - | - | ✅ |
| climateFragmentKoinModule | - | - | ✅ |
| climateMCATTimerFragmentKoinModule | - | - | ✅ |
| climateTabFragmentKoinModule | - | - | ✅ |
| climateTimerFragmentKoinModule | - | - | ✅ |
| scheduleChargeGuidanceViewModule | - | - | ✅ |
| scheduleChargeSettingsViewModule | - | - | ✅ |
| iCupScheduleChargeSettingsViewModule | - | - | ✅ |
| recentLocationPickerViewModule | - | - | ✅ |
| chargeRemindersSettingsViewModule | - | - | ✅ |
| OtaComplete.domainModule | - | - | ✅ |
| otaCompleteViewModule | - | - | ✅ |
| securityFragmentKoinModule | - | - | ✅ |
| nonConnectedAppointmentViewModule | ✅ | - | - |
| vehicleDetailViewModule | ✅ | - | - |
| vehicleWarningsViewModule | ✅ | - | - |
| myCarToolboxViewModule | - | ✅ | - |
| myCarContainerViewModule | - | ✅ | - |
| OrderTracking.koinModules | ✅ | - | - |
| orderSubscriptionKoinModule | ✅ | - | - |
| subscriptionDetailsKoinModule | ✅ | - | - |
| insuranceCardViewModule | ✅ | - | - |
| paymentDetailsKoinModule | ✅ | - | - |
| cbvDocumentsKoinModule | ✅ | - | - |
| pdfViewerActivityModule | - | - | ✅ |
| pdfViewerKoinModule | - | - | ✅ |
