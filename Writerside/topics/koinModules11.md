# koinModules11

```Kotlin
fun koinModules11() =
    tripExportViewModule +
    sentryModule
```
* `tripExportViewModule`
  * This module seems to export drive journal data. This feature is necessary for China region. Need to move to common module
* `sentryModule`
  * This module seems to log crashlytics info.  Looks like this function is provided by the third party library. This can move to Global only
  Also, this module is used in VocApplication `get<InitSentryCrashlyticsUseCase>()()` function. This function is used in the `VOCApplication` class.
  Maybe we can also split this line of code into global-only application. **<font color="red">But if global team wants to know the crashlytics info, we can keep this line of code in the common module.</font>**


|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| `tripExportViewModule` | - | - | ✅ |
| `sentryModule` |  ✅ | - | - |
