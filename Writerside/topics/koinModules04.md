# koinModules04

```Kotlin
fun koinModules04() = listOf(
    toolbarManagerModule,
    widgetKoinModule,
    statisticsViewModule,
    utilsModule,
    chargeStatusViewModule,
    airCleaningKoinModule,
    settingsKoinModule,
    serverConfigKoinModule,
    policyDataSourceModule,
    casAdapterKoinModule,
    locationModule,
    useCaseModule,
    subscriptionsUseCaseModule,
    paymentUseCaseModule,
    invoicesUseCaseModule,
    ecommerceMapperModule,
    supportsNaSubscriptionsUseCaseKoinModule,
    pushTokenRepositoryModule,
    countryAndRegionRepositoryModule,
    cloudMessagingServiceModule,
    pushDomainModule,
    postSignInViewModule,
    postSignInComposeScreenModule,
    inAppFeedbackDataModule,
    inAppFeedbackDomainModule,
) + authViewModule
```

```Kotlin
val authViewModule = listOf(
    signInViewModuleComposeNavigation,
    signInViewKoinModule,
    reSignInViewModule,
    oneTimePasswordViewModule,
    oneTimePasswordViewComposeModule,
    attemptsLimitErrorViewModule,
    resendLimitErrorViewModule,
    accountLockedErrorViewModule,
    noInternetConnectionErrorViewModule,
    sessionExpiredErrorViewModule,
    unknownErrorViewModule,
    serverDownErrorViewModule,
)
```

* `toolbarManagerModule`
  * This module is used to provide the toolbar manager. This module is necessary for the China region. Need to move to common module
* `widgetKoinModule`
  * This module is used to provide the widget. This module is necessary for the China region. Need to move to common module
* `statisticsViewModule`
  * This module is used to provide the statistics view. This module is necessary for the China region. Need to move to common module
* `utilsModule`
  * This module is like used to provide the remote function related utils. Like store climate timer,provide deviceid or some other things. China needs this module. Need to move to common module
* `chargeStatusViewModule`
  * I'm not sure if this ChargeStatusView is or not deprecated.Cause it still use VocMvpFragment. If it is not deprecated, this module is necessary for the China region. Need to move to common module.
* `airCleaningKoinModule`
  * This module is used to provide the air cleaning feature. This module is necessary for the China region. Need to move to common module
* `settingsKoinModule`
  * This module is used to provide secure preference and device secure checking usecase. China also use this module. Need to move to common module
* `serverConfigKoinModule`
  * This module is used to provide the server config (such as build type,dsb server, cnep server and so on). This module is necessary for the China region. Need to move to common module.
* `policyDataSourceModule`
  * This module is used to provide the policy data source. Looks like this module is used in China region. Need to move to China only module
* `casAdapterKoinModule`
  * This module is used to provide the car image adapter. This module is necessary for the China region. Need to move to common module
* `locationModule`
  * This module is used to provide the location. This module is necessary for the China region. Need to move to common module
* `useCaseModule`
  * This module is used to provide the use case(such as set session,restart application,and other remote function related usecase.). This module is necessary for the China region. Need to move to common module
* `subscriptionsUseCaseModule`
  * This module is used to provide the subscriptions use case. China doesn't use this feature. Need to move to global only module
* `paymentUseCaseModule`
  * This module is used to provide the payment use case. China has our own solution. Need to move to global only module
* `invoicesUseCaseModule`
  * This module is used to provide the invoices use case. China doesn't use this feature. Need to move to global only module
* `ecommerceMapperModule`
  * This module is used to provide the ecommerce mapper and related to subscription. China doesn't use this feature. Need to move to global only module.
* `supportsNaSubscriptionsUseCaseKoinModule`
  * This module is used to provide the supports na subscriptions use case. China doesn't use this feature. Need to move to global only module
* `pushTokenRepositoryModule`
  * This module is used to provide the push token repository. China also uses this feature. Need to move to common module
* `countryAndRegionRepositoryModule`
  * This module is used to provide the country and region repository.It used to provide country code in sign in presenter. **Global has already removed this presenter. We China can remove this usage in our next release. We can deprecate this module.**
* `cloudMessagingServiceModule`
  * This module is used to provide the cloud messaging service. China also uses this feature for tsp vehicle push notification. We can move it to China only module
* `pushDomainModule`
  * This module is used to provide the push domain. China need this feature to register device for push. We can move it to common module.
* `postSignInViewModule`
  * China has our owned post-sign in progress. We can move it to global only module
* `postSignInComposeScreenModule`
  * China has our owned post-sign in progress. We can move it to global only module
* `inAppFeedbackDataModule`
* `inAppFeedbackDataModule`
  * These modules are used to provide the in-app feedback data. China doesn't use this feature. Need to move to global only module
* `authViewModule`
  * China has our own sign-in flow. We can move it to global only module


## Conclusion
|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| toolbarManagerModule | - | - | ✅ |
| widgetKoinModule | - | - | ✅ |
| statisticsViewModule | - | - | ✅ |
| utilsModule | - | - | ✅ |
| chargeStatusViewModule | - | - | ✅ |
| airCleaningKoinModule | - | - | ✅ |
| settingsKoinModule | - | - | ✅ |
| serverConfigKoinModule | - | - | ✅ |
| policyDataSourceModule | - | ✅ | - |
| casAdapterKoinModule | - | - | ✅ |
| locationModule | - | - | ✅ |
| useCaseModule | - | - | ✅ |
| subscriptionsUseCaseModule | ✅ | - | - |
| paymentUseCaseModule | ✅ | - | - |
| invoicesUseCaseModule | ✅ | - | - |
| ecommerceMapperModule | ✅ | - | - |
| supportsNaSubscriptionsUseCaseKoinModule | ✅ | - | - |
| pushTokenRepositoryModule | - | - | ✅ |
| countryAndRegionRepositoryModule | - | - | - |
| cloudMessagingServiceModule | - | - | ✅ |
| pushDomainModule | - | - | ✅ |
| postSignInViewModule | ✅ | - | - |
| postSignInComposeScreenModule | ✅ | - | - |
| inAppFeedbackDataModule | ✅ | - | - |
| inAppFeedbackDataModule | ✅ | - | - |
| authViewModule | ✅ | - | - |