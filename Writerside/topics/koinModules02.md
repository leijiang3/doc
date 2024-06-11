# koinModules02

```Kotlin
fun koinModules02() =
    profileModules +
    VocDialog.koinModules +
    ICup.koinModules +
    onboardingSupportModules +
    iCupPairingModules +
    OrderTrackingUI.koinModules +
    DsbDependencies.koinModules +
    addCarViewModule +
    nonConnectedCarManagementViewModule +
    removeNonConnectedCarSuccessViewModule +
    legalDocumentsViewModule +
    pushHandlingDependencies +
    carTabViewModule +
    carTabComposeModule +
    carTabRootModule +
    carDetailsViewModule +
    LegalData.koinModules +
    LegalDomain.koinModules +
    LegalUi.koinModules +
    ProfileData.koinModules +
    ProfileUi.koinModules +
    carStatisticsViewModule
```

```Kotlin
    var profileModules =  listOf(
        viewProfileModule,
        editNameModule,
        editEmailModule,
        editPhoneModule,
        editGenderModule,
        editDateOfBirthModule,
        editAddressModule
)
```
{collapsible="true" collapsed-title="profileModules.Kt"}

```Kotlin
    object VocDialog {
        val koinModules = listOf(
            fullScreenAlertDialogKoinModule
        )
    }
```
{collapsible="true" collapsed-title="VocDialog.koinModules.Kt"}

```Kotlin
    val ICup.koinModules = listOf(
        carSelectionKoinModule,
        iCupDeviceManagerKoinModule,
        connectedCarsKoinModule
    )
```
{collapsible="true" collapsed-title="ICup.koinModules.Kt"}

```Kotlin
    val onboardingSupportModules = Support.koinModules +
        supportUiModule + SupportModule.koinModules

    object SupportModule {
        val koinModules = listOf(
            supportViewModule,
            supportTabRootModule,
            supportTabComposeModule,
            )
    }
    
    val Support.koinModules = listOf(
        supportBaseKoinModule,
        supportActivityModule,
        contactVolvoKoinModule,
        supportPageKoinModule,
        roadsideAssistanceViewModule,
        urgentlyKoinModule,
        chatKoinModule,
        ChatPageKoinModule,
        NativeChatConversationPageKoinModule,
        supportCarSelectorKoinModule,
        supportSearchKoinModule,
        articleDetailKoinModule,
        askFeedbackKoinModule,
        thanksFeedbackKoinModule
    )
```
{collapsible="true" collapsed-title="onboardingSupportModules.Kt"}

```Kotlin
    val iCupPairingModules = ICupPairingData.koinModules +
    ICupPairingDomain.koinModules +
    ICupPairingUI.koinModules
    
    object ICupPairingData {

    val koinModules = listOf(
            iCupPairingDataModule,
        )
    }

    object ICupPairingDomain {
    
        val koinModules = listOf(
            iCupPairingDomainModule,
        )
    }
    object ICupPairingUI {

        val koinModules = listOf(
            iCupPairingViewModule,
            iCupPairingUserGuideViewModule,
            iCupPairingNoRelationFoundViewModule,
            reestablishConnectionGuideViewModule,
            dataSharingActivationViewModule
        )
    }

```
{collapsible="true" collapsed-title="iCupPairingModules.Kt"}

```Kotlin
object OrderTrackingUI {

    val koinModules = listOf(
        orderTrackingLandingViewModule,
        orderTrackingDetailsViewModule,
        orderTrackingWelcomeViewModule,
        orderTrackingTimelineViewModule,
    )
}

```
{collapsible="true" collapsed-title="OrderTrackingUI.koinModules.kt"}


* `profileModules`
  * China has it's own profile module, which is different from the global profile module. these modules could move to global only modules.

* `VocDialog.koinModules`
  * This is a full screen dialog, used for notice user when the vehicle relationship is broken. China is also use this dialog, this can move to common modules.
* `ICup.koinModules`
  * This is a module for the iCup feature, China is also using this feature, this can move to common modules.

* `onboardingSupportModules` **Looks like those modules is all related global support views. This doesn't used in china feature. They all can move to Global Only**
  * `supportViewModule`
  * `supportTabRootModule`
  * `supportTabComposeModule`
  * `supportUiModule`
  * `supportBaseKoinModule`
  * `supportActivityModule`
  * `contactVolvoKoinModule`
  * `supportPageKoinModule`
  * `roadsideAssistanceViewModule`
  * `urgentlyKoinModule`
  * `chatKoinModule`
  * `ChatPageKoinModule`
  * `NativeChatConversationPageKoinModule`
  * `supportCarSelectorKoinModule`
  * `supportSearchKoinModule`
  * `articleDetailKoinModule`
  * `askFeedbackKoinModule`
  * `thanksFeedbackKoinModule` 
* `iCupPairingModules`
  * This module is related to icup device pairing , China need this modules to connect with icup and should move to common modules.
* `OrderTrackingUI.koinModules`
  * This module is related to the order tracking feature, China has it's own order tracking feature, this module should move to global only modules.
* `DsbDependencies.koinModules`
  * This module is related to the DSB feature, China has it's own DSB feature, this module should move to global only modules.
* `addCarViewModule`
  * This list of modules are related to connect a new vehicle . China need these modules and should move to common modules.
* `nonConnectedCarManagementViewModule`
  * This list of modules are related to manage the non connected vehicles. China need these modules and should move to common modules.


|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| `profileModules` | ✅ | - | - |
| `VocDialog.koinModules` |  - | - | ✅ |
| `ICup.koinModules` |  - | - | ✅ |
| `onboardingSupportModules` | ✅ | - | - |
| `iCupPairingModules` | - | - | ✅ |
| `OrderTrackingUI.koinModules` | ✅ | - | - |
| `DsbDependencies.koinModules` | ✅ | - | - |
| `addCarViewModule` | - | - | ✅ |
| `nonConnectedCarManagementViewModule` | - | - | ✅ |
