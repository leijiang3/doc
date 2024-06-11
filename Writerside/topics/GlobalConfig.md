# GlobalConfig

## VccServer
```Kotlin
sealed class VccServer(
    val baseUrl: String,
    val apiKey: String
) {

    object PROD : VccServer(
        baseUrl = "https://gw.consumer.api.volvocars.com",
        apiKey = "855fec8628e14ba69b0bd8d6a71af78c"
    ) {
        override fun toString() = "PROD"
    }

    object QA : VccServer(
        baseUrl = "https://gw.qa.consumer.api.volvocars.com",
        apiKey = "823c8c1c5bf9466c9953ec30013e1003"
    ) {
        override fun toString() = "QA"
    }

    object DEV : VccServer(
        baseUrl = "https://test2-emea-apim.azure-api.net",
        apiKey = "NO API KEY"
    ) {
        override fun toString() = "DEV"
    }

    class MOCK(baseUrl: String, apiKey: String) : VccServer(baseUrl, apiKey) {
        override fun toString() = "MOCK($baseUrl)"
    }
}
```
{collapsible="true"}


## HeaderConfig
```Kotlin
    typealias uaHeader:UAHeader = header("User-Agent","vca-android/${getBuildVersionUseCase().versionName}")
    typealias authHeader:AuthHeader = header("Authorization", "Bearer $authToken")
```



```cURL
curl --request GET \
  --url https://cnepmob.volvocars.com/ \
  --header 'Accept: application/volvo.cloud.cnepmob.v1+json' \
  --header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IlFWVzI2OHJuSlZGdHh2cUs5c214elRwUjlBVV9SUzI1NiIsInBpLmF0bSI6ImYifQ.eyJzY29wZSI6Im9wZW5pZCBlbWFpbCBwcm9maWxlIGNhcmVfYnlfdm9sdm86ZmluYW5jaWFsX2luZm9ybWF0aW9uOmludm9pY2U6cmVhZCBjYXJlX2J5X3ZvbHZvOmZpbmFuY2lhbF9pbmZvcm1hdGlvbjpwYXltZW50X21ldGhvZCBjYXJlX2J5X3ZvbHZvOnN1YnNjcmlwdGlvbjpyZWFkIGN1c3RvbWVyOmF0dHJpYnV0ZXMgY3VzdG9tZXI6YXR0cmlidXRlczp3cml0ZSBvcmRlcjphdHRyaWJ1dGVzIHZlaGljbGU6YXR0cmlidXRlcyB0c3BfY3VzdG9tZXJfYXBpOmFsbCB2b2x2b19vbl9jYWxsOmFsbCIsImNsaWVudF9pZCI6ImNoaW5haWFtIiwiaXNzIjoiaHR0cHM6Ly92b2x2b2lkLmNuLnZvbHZvY2Fycy5jb20iLCJhdWQiOiJhaFA3ZTQiLCJtYXJrZXQiOiJDTiIsImZpcnN0TmFtZSI6IlVua25vd24iLCJsYXN0TmFtZSI6IlVua25vd24iLCJzdWIiOiIzMzYxNzNiNi1lMjIwLTQyNjctYjRmYi1mZTM0MzVkZTc3ZDYiLCJlbWFpbCI6Iis4NjEzODE3MTIwMDQ2IiwiZXhwIjoxNzEwNzQ0NzMyfQ.aNR8tqcA6cERkN1wyNUdqGX4XmKTdtQyqmvq1umzBkn6gUo2LM0yHq-14PIrrTKRW-NSUxMZlszsHZzNpB9CrU-JPNKkc2-ah2G7DS_0L2IiaEHIsYMuHxJwzBgJ_8KHedtVJH-eKW5wfopQORTxeHqtj76F1irdloyiJlkeFBhSSrFydQoOcg1ILlYJaNr8ZtFZKUwft7bsmF9lfk3XH83OaebIqNux0AFr08mFzMi6iXWEZzOMsvIZ9lw2XOptQzmh2myYs3xKCuHp9n1goIRl4vuxUHQ22KMTPDHi5IBrcH4qMk5x-lLn9BXxisfZHxTeVzo4WdQdKyNPyzktcQ' \
  --header 'User-Agent: vca-android/5.37.0'
```

```json
{
	"c3": {
		"url": "https://cepmobtoken.prod.c3.volvocars.com.cn",
		"grpcHost": "cepmobtoken.prod.c3.volvocars.com.cn",
		"grpcPort": 443,
		"grpcKeepAliveTime": 45
	},
	"c3Lbs": {
		"url": "https://cepmobtoken.prod.c3.volvocars.com.cn",
		"grpcHost": "cepmobtoken.prod.c3.volvocars.com.cn",
		"grpcPort": 443,
		"grpcKeepAliveTime": 45
	}
}
```


## TspServer
```Kotlin
    CHINA_QA("https://vocapi.cn.qa.vocw.cn"),
    CHINA_PROD("https://vocapi.cn.prod.vocw.cn")
```
Start typing here...