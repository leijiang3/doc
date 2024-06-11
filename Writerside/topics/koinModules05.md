# koinModules05
```kotlin
fun koinModules05() = listOf(
    UserModule.domain,
    UserModule.data,
    validateVinUseCaseKoinModule,
    appLifeCycleModule,
    serviceHistoryModule,
    serviceHistoryRepositoryModule,
    serviceHistoryUseCaseModule,
    subscriptionListPARCHViewModule,
    subscriptionDetailsModule,
    vehicleImageKoinModule,
    casModule,
    policyUpdateLoadViewModule,
    policyUpdateCNViewModule,
    renewSubscriptionViewModule,
    inputPinViewModule,
    newPinViewModule,
    nonConnectedIntroViewModule,
    nonConnectedHomeKoinModule,
    profileTabUseCaseModule,
    vehicleDetailsKoinModule,
    batteryChargeTimerUseCaseModule,
    fragmentFactoryModule,
    chargeLocationsUseCaseModule,
    saveNewTspChargeTimerUseCaseModule,
    editTspChargeTimerUseCaseModule,
    deleteTspChargeTimerUseCaseModule,
    getNewTspChargingLocationsUseCaseModule,
    getIsAcceptedChargingLocationsServiceRunningUseCaseModule,
    getIsNewChargingLocationsServiceRunningUseCaseModule,
    deleteTspRecentLocationUseCaseModule,
    startTspChargingNowUseCaseModule,
    getTspStatusUseCaseModule,
)
```

* `UserModule.domain` 
* `UserModule.data` 
  * These two modules are provide the domain and data layer dependencies for the user feature.Related account profile. 
  This should move to the common modules
* `validateVinUseCaseKoinModule`
  * This module provides the dependencies for the validate vin use case. Used in pairing flow. Should move to the common modules
* `appLifeCycleModule`
  * This module provides the dependencies for the app lifecycle. Used in OTA installation.Should move to the common modules
* `serviceHistoryModule`
* `serviceHistoryRepositoryModule`
* `serviceHistoryUseCaseModule`
  * These three modules are provide the dependencies for the service history feature.**I've no idea what are they used for,I didn't see this feature in China app**
* `subscriptionListPARCHViewModule`
* `subscriptionDetailsModule`
  * These two modules are provide the dependencies for the subscription feature. China has it's own subscription feature,so these two modules should move to the global only module
* `vehicleImageKoinModule`
* `casModule`
  * These two modules are provide the dependencies for the vehicle image and cas feature. Also `vehicleImageKoinModule` was marked as deprecated, but still used in the codebase. Should move to the common module
* `policyUpdateLoadViewModule`
* `policyUpdateCNViewModule`
  * For these two modules, `policyUpdateLoadViewModule` is used in the policy update feature globally.This should move to global only modules
, and `policyUpdateCNViewModule` is used in the policy update feature for China. Should move to the china only module
* `renewSubscriptionViewModule`
  * This module is provide the dependencies for the renew subscription feature. Should move to the global only module
* `inputPinViewModule`
* `newPinViewModule`
  * These two modules are used in pairing flow. Should move to the common modules
* `nonConnectedIntroViewModule`
* `nonConnectedHomeKoinModule`
  * These two modules are used in the non connected feature. Should move to the common module
* `profileTabUseCaseModule`
  * This module is tricky. Although it's named `profileTabUseCaseModule`, it provides a factory for `ShowSubscriptionsUseCase`, 
  which has methods used to determine if a vehicle is already connected.Anyway, this module is only used for `ProfileTabView`, we china app doesn't have this feature, 
  so this should move to the global only module
* `vehicleDetailsKoinModule`
  * This module is used in the vehicle details feature. And this is a analytics module, should move to the common module
  **I'm not sure if this analytics module is still used in global app. Seems this is very legacy car detail view related**
* `batteryChargeTimerUseCaseModule`
  * This module is used in the battery charge timer feature related vocmo repository. Should move to the common module
* `fragmentFactoryModule`
  * This module is used to route legacy fragment. Currently it should move to the common module
* `chargeLocationsUseCaseModule`
* `saveNewTspChargeTimerUseCaseModule`
* `editTspChargeTimerUseCaseModule`
* `deleteTspChargeTimerUseCaseModule`
* `getNewTspChargingLocationsUseCaseModule`
* `getIsAcceptedChargingLocationsServiceRunningUseCaseModule`
* `getIsNewChargingLocationsServiceRunningUseCaseModule`
* `deleteTspRecentLocationUseCaseModule`
* `startTspChargingNowUseCaseModule`
* `getTspStatusUseCaseModule`
  * These modules are all related remote function. Should move to the common module


### Conclusion


|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| UserModule.domain | - | - | ✅ |
| UserModule.data | - | - | ✅ |
| validateVinUseCaseKoinModule | - | - | ✅ |
| appLifeCycleModule | - | - | ✅ |
| serviceHistoryModule | ? | ? | ? |
| serviceHistoryRepositoryModule | ? | ? | ? |
| serviceHistoryUseCaseModule | ? | ? | ? |
| subscriptionListPARCHViewModule | ✅ | - | - |
| subscriptionDetailsModule | ✅ | - | - |
| vehicleImageKoinModule | - | - | ✅ |
| casModule | - | - | ✅ |
| policyUpdateLoadViewModule | ✅ | - | - |
| policyUpdateCNViewModule | - | ✅ |
| renewSubscriptionViewModule | ✅ | - | - |
| inputPinViewModule | - | - | ✅ |
| newPinViewModule | - | - | ✅ |
| nonConnectedIntroViewModule | - | - | ✅ |
| nonConnectedHomeKoinModule | - | - | ✅ |
| profileTabUseCaseModule | ✅ | - | - |
| vehicleDetailsKoinModule | ✅ | - | - |
| batteryChargeTimerUseCaseModule | - | - | ✅ |
| fragmentFactoryModule | - | - | ✅ |
| chargeLocationsUseCaseModule | - | - | ✅ |
| saveNewTspChargeTimerUseCaseModule | - | - | ✅ |
| editTspChargeTimerUseCaseModule | - | - | ✅ |
| deleteTspChargeTimerUseCaseModule | - | - | ✅ |
| getNewTspChargingLocationsUseCaseModule | - | - | ✅ |
| getIsAcceptedChargingLocationsServiceRunningUseCaseModule | - | - | ✅ |
| getIsNewChargingLocationsServiceRunningUseCaseModule | - | - | ✅ |
| deleteTspRecentLocationUseCaseModule | - | - | ✅ | 
| startTspChargingNowUseCaseModule | - | - | ✅ |
| getTspStatusUseCaseModule | - | - | ✅ |



