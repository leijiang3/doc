# composableComponentsModule
```Kotlin
val composeNavigationModules
    get() = listOf(
        routeActivityModule,
        mainComposeActivityModule,
        navHostControllerNavigationModule,
        environmentSelectionBottomSheetViewModule,
        regionSelectionBottomSheetViewModule,
        globalBottomTabModule,
    )
```

* `routeActivityModule`
  * For now, China still use StartActivity for the route, and we still didn't adopt the global route,
  Although we have a plan to adopt the global route, we still need to keep this module and this can move to common module
* `mainComposeActivityModule`
  *  We are adopting the global main activity, this can move to common module.
* `navHostControllerNavigationModule`
  * We are adopting the global navigation, this can move to common module. 
* `environmentSelectionBottomSheetViewModule`
    * China has our own environment selection View, this can move to global only modules.
* `regionSelectionBottomSheetViewModule`
  * China has our own region selection View, this can move to global only modules.
* `globalBottomTabModule`
  * Looks like this is the configurable bottom tab that we all expected to use. But this is just defined Global bottom tabs.
  **I believe we China can define our own bottom tabs. This can move to global only modules.**

|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| `routeActivityModule` | - | - | ✅ |
| `mainComposeActivityModule` | - | - | ✅ |
| `navHostControllerNavigationModule` | - | - | ✅ |
| `environmentSelectionBottomSheetViewModule` | ✅ | - | - |
| `regionSelectionBottomSheetViewModule` | ✅ | - | - |
| `globalBottomTabModule` | ✅ | - | - |
