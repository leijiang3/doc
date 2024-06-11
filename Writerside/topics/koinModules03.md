# koinModules03

```Kotlin
fun koinModules03() = listOf(
    vccExternalAPINetworkModule,
    parkopediaClientModule,
    aqiClientModule,
    hereWeatherClientModule,
    weatherModule,
    sessionKoinModule,
    sessionModule,
    analyticsModule,
    bottomTabsActivityModule,
    homeTabModule,
    startActivityModule,
    modalActivityModule,
    feedbackActivityModule,
    standAloneActivityModule,
    newPairingActivityModule,
    cloudTermsAndConditionsActivityModule,
    welcomeViewModule,
    regionSelectionViewModuleLegacyNavigation,
    otaErrorViewModule,
    guidesFeedKoinModule,
    feedbackModule,
    climateEditTimerDaysFragmentKoinModule,
    pushSettingsModule,
)
```

* `vccExternalAPINetworkModule`
  * This module is just a retrofit and okHttp client. This module is used to make network calls to the VCC external API. 
  It looks like this is for AQI, Weather, and Parkopedia. This module is necessary for the China region. Need to move to common module
* `parkopediaClientModule`
  * This module is used to make network calls to the Parkopedia API.  Sounds like this api is used for get parking spots globally. Maybe it's used in find my car. This module is necessary for the China region. Need to move to common module.
  also,**in the feature, do we have a chance to migrate to our China owned parking api? from AMap? @Rui**
* `aqiClientModule`
  * This module is used to make network calls to the AQI API. This module is necessary for the China region. Need to move to common module
* `hereWeatherClientModule`
  * This module is used to make network calls to the Here Weather API. This module is necessary for the China region. Need to move to common module
* `weatherModule`
  * This module is used to provide weather data. It will provide weather data by region. It will show the aqi and weather data. This module is necessary for the China region. Need to move to common module
* `sessionKoinModule`
  * This module is used to provide setting, tsp account relationship, weather utils and so on. This module is necessary for the China region. Need to move to common module
* `sessionModule`
  * This module is used to provide the current vehicle session. This module is necessary for the China region. Need to move to common module
* `analyticsModule`
  * This module is used to provide analytics. China dependent this module to resend the analytics data. This module is necessary for the China region. Need to move to common module
* `bottomTabsActivityModule`
  * This module is used to provide the bottom Tabs activity. This module is necessary for the China region. Need to move to common module
* `homeTabModule`
  *  This module is duplicate with `koinModules01.homeTabModule`. This module is necessary for the China region. Need to move to common module
* `startActivityModule`
  * This module is used to provide the start activity. I noticed that global will deprecate this Activity and use `CommonComppseActivity`. This module is now necessary for the China region.
  **We are migrating this to Our owned ComposeStartActivity(already started,on a single decouple branch). But currently,Need to move to common module.**
* `modalActivityModule`
  * **I'm not sure about this module.**  It's also an Activity for climate,pre cleaning, and so on. 
* `feedbackActivityModule`
  * China has our own feedback fragment, So this module is not necessary for China region. It can move to global only modules. Also, maybe global will deprecate this Activity?
* `standAloneActivityModule`
  * This module is used to provide the StandAlone Activity. This module is necessary for the China region. Need to move to common module
* `newPairingActivityModule`
  * This module is used to provide PairingFlow Activity. I know Global Team has already deprecated this Activity. In our China , we still use it right now. **But I can guarantee that we can remove it in our next release.**
* `cloudTermsAndConditionsActivityModule`
  * This module seems to Show the terms and conditions update info. I believed China has already had our own terms and condition feature. It can move to global only modules.
* `welcomeViewModule`
  * This is a WelcomeView. China have our own welcome view. and this can move to global only modules.
* `regionSelectionViewModuleLegacyNavigation`
  * This module is used to provide the region selection view. In our China , we can hardcode the region to CN. This module is not necessary for China region. It can move to global only modules.
* `otaErrorViewModule`
  * This module is used to provide the OTA error view. This module is necessary for the China region. Need to move to common module
* `guidesFeedKoinModule`
  * This module is used to provide the feedback feature. This module is not necessary for the China region. Need to move to global only module
* `feedbackModule`
  * This module is used to provide the feedback feature. This module is not necessary for the China region. Need to move to global only module
* `climateEditTimerDaysFragmentKoinModule`
  * This is belonged to `ClimateEditTimerFragment` feature. Sounds like this is used for climate control feature. 
  This module is necessary for the China region. Need to move to common module.

|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| `vccExternalAPINetworkModule` | - | - | ✅ |
| `parkopediaClientModule` | - | - | ✅ |
| `aqiClientModule` | - | - | ✅ |
| `hereWeatherClientModule` | - | - | ✅ |
| `weatherModule` | - | - | ✅ |
| `sessionKoinModule` | - | - | ✅ |
| `sessionModule` | - | - | ✅ |
| `analyticsModule` | - | - | ✅ |
| `bottomTabsActivityModule` | - | - | ✅ |
| `homeTabModule` | - | - | ✅ |
| `startActivityModule` | - | - | ✅ |
| `modalActivityModule` | - | - | ✅ |
| `feedbackActivityModule` | ✅ | - | - |
| `standAloneActivityModule` | - | - | ✅ |
| `newPairingActivityModule` | - | - | ✅ |
| `cloudTermsAndConditionsActivityModule` | ✅ | - | - |
| `welcomeViewModule` | ✅ | - | - |
| `regionSelectionViewModuleLegacyNavigation` | ✅ | - | - |
| `otaErrorViewModule` | - | - | ✅ |
| `guidesFeedKoinModule` | ✅ | - | - |
| `feedbackModule` | ✅ | - | - |
| `climateEditTimerDaysFragmentKoinModule` | - | - | ✅ |


## Notes
I don’t remember very clearly. It seems like a long time ago we received a request to 
open this feature for our internal staff who handle vehicle allocations, but it seems like 
it was abandoned later. Actually, I’m not very sure if these two koins(`guidesFeedKoinModule`,`feedbackModule`) can really be removed.

