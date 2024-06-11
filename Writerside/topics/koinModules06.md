# koinModules06

```Kotlin
fun koinModules06() = listOf(
    carLocksViewKoinModule,
    carLocksComposeKoinModule,
    remoteControlFeedbackUseCaseModule,
    Permissions.domainModule,
    startModule,
    startViewModule,
    applicationCoroutineScopeModule,
    deepLinkIntentModule,
    dataSharingRepositoryModule,
    translationExtensionModule,
    FeedbackPrivacyNotice.domainModule,
    FeedbackPrivacyNotice.viewModule,
    privacySettingsViewModule,
    legacyReleaseNotesNavigatorModule,
    carLocatorModule,
    legacyOtaInAppMessageHelperModule,
    carHomeUseCaseModule,
    digitKey3CGuideViewModule,
    digitKeyDetailViewModule,
    digitKeyViewModule,
    digitalKeyBleViewModule,
    digitalKeyBleGuideViewModule,
    digitalKeyBleShareGuideViewModule,
    digitalKeyBlePermissionViewModule,
    digitalKeyProblemDiagnosisViewModule,
    beUnboundViewModule,
    ecarxTheftNotification,
    ecarxNotificationSettingModule,
)
```
* `carLocksViewKoinModule`
    * This module is used to provide the car locks view. This module is necessary for the China region. Need to move to common module
* `carLocksComposeKoinModule`
    * This module is used to provide the car locks compose view. This module is necessary for the China region. Need to move to common module
* `remoteControlFeedbackUseCaseModule`
    * This module is used to provide the remote control feedback use case. **Same as the feedback modules before.**
* `Permissions.domainModule`
  * This provide a use-case to request permissions. China needs this module. Need to move to common module
* `startModule`
  * This module is used for StartFragment to perform a click event to navigate to SignInView. China doesn't need this module.Also global has already deprecated StartFragment? Maybe we can directly remove this module.
* `startViewModule`
  * Global team has already migrate this fragment to compose. China doesn't need this module. **If StartFragment is deprecated**, this module can be removed.
* `applicationCoroutineScopeModule`
  * This module is used to provide the application coroutine scope. **I'm not sure where it has been used.**
* `deepLinkIntentModule`
  * This module is used to handle deep link. It was used in StartFragment. Aslo APAC Team use it in BottomTabsActivity. So currently, it should move to common module.
* `dataSharingRepositoryModule`
  * This module is used to provide the data sharing status. It's related to remote control function. It's necessary for the China region. Need to move to common module
* `translationExtensionModule`
  * This module is used to provide the string format utils. This module is necessary for the China region. Need to move to common module
* `FeedbackPrivacyNotice.domainModule`
* `FeedbackPrivacyNotice.viewModule`
  * This module is used to provide the feedback privacy notice. This module is necessary for the China region. Need to move to common module
* `privacySettingsViewModule`
  * This module is used to provide the privacy settings view. Looks like something related to data sharing and authenticated applications. If related data sharing,We China use this too. Should move to common module
  * ![image_14.png](image_14.png)
* `legacyReleaseNotesNavigatorModule`
  * This module is used to provide the legacy release notes navigator. This module is necessary for the China region. Need to move to common module
* `carLocatorModule`
  * This module is used to related to car locator（find my car）. This module is necessary for the China region. Need to move to common module
* `legacyOtaInAppMessageHelperModule`
  *  From the codebase, It seems this module is used to identify a propulsion type for a vehicle. **I'm not sure about this module.**
* `carHomeUseCaseModule`
  * This module is used to provide the car home use case,such as app state, car state, car nickname,car offline status. This module is necessary for the China region. Need to move to common module
* `digitKey3CGuideViewModule`
* `digitKeyDetailViewModule`
* `digitKeyViewModule`
* `digitalKeyBleViewModule`
* `digitalKeyBleGuideViewModule`
* `digitalKeyBleShareGuideViewModule`
* `digitalKeyBlePermissionViewModule`
* `digitalKeyProblemDiagnosisViewModule`
* `beUnboundViewModule`
* `ecarxTheftNotification`
* `ecarxNotificationSettingModule`
  * Apac team provides these modules. These modules are used only in China region. So it must move to china-only module



## Conclusion
|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| carLocksViewKoinModule | - | - | ✅ |
| carLocksComposeKoinModule | - | - | ✅ |
| remoteControlFeedbackUseCaseModule | - | - | ✅ |
| Permissions.domainModule | - | - | ✅ |
| startModule | ✅ | - | - |
| startViewModule | ✅ | - | - |
| applicationCoroutineScopeModule | - | - | ✅ |
| deepLinkIntentModule | - | - | ✅ |
| dataSharingRepositoryModule | - | - | ✅ |
| translationExtensionModule | - | - | ✅ |
| FeedbackPrivacyNotice.domainModule | - | - | ✅ |
| FeedbackPrivacyNotice.viewModule | - | - | ✅ |
| privacySettingsViewModule | - | - | ✅ |
| legacyReleaseNotesNavigatorModule | - | - | ✅ |
| carLocatorModule | - | - | ✅ |
| legacyOtaInAppMessageHelperModule | - | - | ✅ |
| carHomeUseCaseModule | - | - | ✅ |
| digitKey3CGuideViewModule | - | ✅ | - |
| digitKeyDetailViewModule | - | ✅ | - |
| digitKeyViewModule | - | ✅ | - |
| digitalKeyBleViewModule | - | ✅ | - |
| digitalKeyBleGuideViewModule | - | ✅ | - |
| digitalKeyBleShareGuideViewModule | - | ✅ | - |
| digitalKeyBlePermissionViewModule | - | ✅ | - |
| digitalKeyProblemDiagnosisViewModule | - | ✅ | - |
| beUnboundViewModule | - | ✅ | - |
| ecarxTheftNotification | - | ✅ | - |
| ecarxNotificationSettingModule | - | ✅ | - |