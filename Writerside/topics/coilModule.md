# coilModule

```Kotlin
fun coilModule() = module {
    single {
        val quarter = 0.25
        val memory = 512L * 1024 * 1024 // 512MB
        val cacheFolder = "image_cache"

        val appContext = androidApplication()

        val interceptors = if (BuildConfig.DEBUG) {
            arrayOf(vcaUserAgent(), loggerInterceptor)
        } else {
            arrayOf(vcaUserAgent())
        }

        ImageLoader.Builder(appContext)
            .okHttpClient {
                buildHttpClient(interceptors = interceptors)
            }
            .networkObserverEnabled(true)
            .memoryCache {
                MemoryCache.Builder(appContext)
                    // Set the max size to 25% of the app's available memory.
                    .maxSizePercent(quarter)
                    .build()
            }
            .diskCache {
                DiskCache.Builder()
                    .directory(appContext.filesDir.resolve(cacheFolder))
                    .maxSizeBytes(memory)
                    .build()
            }
            .components {
                if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.P) {
                    add(ImageDecoderDecoder.Factory())
                } else {
                    add(GifDecoder.Factory())
                }
            }
            // Show a short crossfade when loading images asynchronously.
            .crossfade(true)
            // Enable logging to the standard Android log if this is a debug build.
            .apply { if (BuildConfig.DEBUG) logger(DebugLogger()) }
            .build()
    }
}
```
{collapsed-title="Coil Init module" collapsible="true" }

This module is used for coil initialization. China app also use this to load images. 
Such as release note. This could be a common module.


|:------:|:------:|:------:|:------:|:------:|:------:|
| Module Name | Global Only | China Only | Common Module |
| coilModule | - | - | ✅ |
