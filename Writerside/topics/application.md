# application

```Kotlin
    override fun onCreate() {
        super.onCreate()
        // Temp fix until all references to BaseApplication APPLICATION are removed.
        if (Build.FINGERPRINT == "robolectric") {
            return
        }

        crashReporter.init()

        setupCrashCatcher()

        ProcessLifecycleOwner.get().lifecycle.addObserver(AppLifecycleListener())

        setLogger()

        EcarxHeartBeatUtils.initHeartBeatARouter(this)

        logd(TAG, "OnCreate")

        setupAnalytics()

        registerActivityLifecycleCallbacks(this)

        CountryNameUtil.initializeValues(this)

        DokitHelper.initialize(this)

        startKoin()

        setupServerConfig()

        loadBuildFeatureFlags()

        configureGoogleDataServices()

        get<InitObservabilityUseCase>()()

        get<InitSentryUseCase>()()

        applicationScope.launch {
            get<InitializeInAppFeedbackUseCase>()()
        }

        get<StartPublishingAppLifeCycleChangesUseCase>().invoke()

        setImageLoader()
    }

```
{collapsible="true" collapsed-title="VocApplication.kt" }


```Kotlin
crashReporter.init()
configureGoogleDataServices()
get<InitObservabilityUseCase>()()
get<InitSentryUseCase>()()
applicationScope.launch {
   get<InitializeInAppFeedbackUseCase>()()
}
```



```Kotlin
EcarxHeartBeatUtils.initHeartBeatARouter(this)
CountryNameUtil.initializeValues(this)
DokitHelper.initialize(this)
```
These should be moved to China only Application




```Kotlin
  loadBuildFeatureFlags()
```
We received earlier that we need to enforce the market as “cn” 
in the Chinese region. Some modifications may be necessary here.

