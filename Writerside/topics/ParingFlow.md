# PairingFlow

- 当用户需要在app中激活车控时，需要构造一个PairCarModalDestination跳转到激活流程中的第一步

``` Kotlin
data class PairCarModalDestination(
    val vin: String?,
) : Destination
```
{collapsible="true"}


- 监听传递来的VIN或者用户输入的VIN (ValidateVinFormatUseCase.kt)
  - 当 ValidateVinFormatUseCase 返回为true时,进入下一步

  - 以当前的VIN去检查车辆是否已经被激活 (GetPairedVehicleUseCase.kt)
    - 数据已经在启动app时从C3/WLC/VOCMO 获取过
    - 数据存储在VehicleRepository.kt中

    - 如果车辆已经被激活，跳转到车辆已经被激活弹窗，如果没有，则开始加载车辆车图
	  {collapsible="true"}
      ```
          curl --request GET \
            --url 'https://gw.consumer.api.volvocars.com/cas/visualizations/vehicles/LYVXEEDE8ML489754?client=vocapp' \
            --header 'Accept: application/vnd.volvocars.api.configuratorassetservice.visualization.v1+json' \
            --header 'Accept-Language: en-CN' \
            --header 'VCC-Api-Key: 855fec8628e14ba69b0bd8d6a71af78c'
       ```
{collapsible="true"}
返回结果Json如下

 ```json
{
	"Combinations": [
		{
			"VisualizedFeatures": {
				"FuelportChargingport": "CB04",
				"207": "CJ07",
				"Gearlever": "DI03",
				"SunRoof": "EV02",
				"Ceiling": "FH01",
				"Roof": "FN02",
				"Grille": "GR08",
				"Headlights": "JB0A",
				"Foglight": "JT02",
				"SoundSystem": "K502",
				"FrontStorage": "K903",
				"Mirror": "LF05",
				"Decor": "NC0D",
				"SeatCount": "NP02",
				"InteriorIllumination": "PD02",
				"Rims": "R171",
				"SteeringWheel": "RU0A",
				"EngineType": "T101",
				"EngineEmblem": "T21A",
				"Handles": "TC06",
				"Skidplate": "TJ02",
				"Decorsidewindow": "TM04",
				"Rails": "TP05",
				"Salesversion": "R6",
				"Transmission": "E",
				"SteeringType": "1",
				"Color": "70700",
				"Upholstery": "RB0000"
			},
			"VisualizedFeatureIcons": {
				"Gearlever": "{baseUrl}/image/v2/icons/MY21_2017/536/104/E/DI03.{format}?client=vocapp",
				"Decor": "{baseUrl}/image/v2/icons/MY21_2017/536/101/NC0D.{format}?client=vocapp",
				"Rims": "{baseUrl}/image/v2/icons/MY21_2017/536/102/R171.{format}?client=vocapp",
				"SteeringWheel": "{baseUrl}/image/v2/icons/MY21_2017/536/105/RU0A.{format}?client=vocapp",
				"Color": "{baseUrl}/image/v2/icons/MY21_2017/536/10/70700.{format}?client=vocapp",
				"Upholstery": "{baseUrl}/image/v2/icons/MY21_2017/536/11/RB0000.{format}?client=vocapp"
			},
			"Views": {
				"exterior": {
					"UrlTemplate": "{baseUrl}/image/dynamic/MY21_2017/536/exterior-v1/R6/70700/R171/FN02/_/TC06/TP05/_/JT02/GR08/T101/TJ02/TM04/_/CB04/EV02/JB0A/T21A/LF05/_/_/_/_/_/_/_/{profile}.{format}?market=cn&client=vocapp",
					"Resolution": {
						"Width": 4898,
						"Height": 2756
					},
					"UrlTemplateParameters": {
						"profile": {
							"Required": true,
							"Values": [
								"default",
								"Grille",
								"Headlights",
								"Taillight",
								"FrontRim",
								"RearWindowTrim",
								"SideModelpage",
								"Banner"
							]
						}
					},
					"QueryParameters": {
						"angle": {
							"Required": false,
							"Values": [
								"1",
								"3",
								"4",
								"5",
								"6",
								"7",
								"100",
								"103",
								"104",
								"105",
								"106",
								"107"
							]
						},
						"bg": {
							"Required": false,
							"Values": [
								"descriptive-studio"
							]
						}
					}
				},
				"interior": {
					"UrlTemplate": "{baseUrl}/image/dynamic/MY21_2017/536/interior-v2/R6/E/RB0000/NC0D/DI03/RU0A/_/PD02/NP02/CB04/EV02/K502/K903/FH01/_/_/{profile}.{format}?market=cn&client=vocapp",
					"Resolution": {
						"Width": 4898,
						"Height": 2756
					},
					"UrlTemplateParameters": {
						"profile": {
							"Required": true,
							"Values": [
								"default"
							]
						}
					},
					"QueryParameters": {
						"angle": {
							"Required": false,
							"Values": [
								"0"
							]
						}
					}
				},
				"drivers-view": {
					"UrlTemplate": "{baseUrl}/image/dynamic/MY21_2017/536/drivers-view-v2/R6/E/RB0000/NC0D/DI03/RU0A/_/PD02/NP02/CB04/EV02/K502/K903/FH01/_/_/{profile}.{format}?market=cn&client=vocapp",
					"Resolution": {
						"Width": 4898,
						"Height": 2756
					},
					"UrlTemplateParameters": {
						"profile": {
							"Required": true,
							"Values": [
								"default",
								"GearShift",
								"SteeringWheel"
							]
						}
					},
					"QueryParameters": {
						"angle": {
							"Required": false,
							"Values": [
								"0",
								"100"
							]
						}
					}
				},
				"rear-view": {
					"UrlTemplate": "{baseUrl}/image/dynamic/MY21_2017/536/rear-view-v2/R6/E/RB0000/NC0D/DI03/PD02/NP02/CB04/EV02/FH01/_/_/{profile}.{format}?market=cn&client=vocapp",
					"Resolution": {
						"Width": 4898,
						"Height": 2756
					},
					"UrlTemplateParameters": {
						"profile": {
							"Required": true,
							"Values": [
								"default",
								"Fabric"
							]
						}
					},
					"QueryParameters": {
						"angle": {
							"Required": false,
							"Values": [
								"0",
								"100"
							]
						}
					}
				},
				"deco-view": {
					"UrlTemplate": "{baseUrl}/image/dynamic/MY21_2017/536/deco-view-v1/RB0000/NC0D/PD02/NP02/CB04/EV02/K502/FH01/_/{profile}.{format}?market=cn&client=vocapp",
					"Resolution": {
						"Width": 4898,
						"Height": 2756
					},
					"UrlTemplateParameters": {
						"profile": {
							"Required": true,
							"Values": [
								"default"
							]
						}
					},
					"QueryParameters": {
						"angle": {
							"Required": false,
							"Values": [
								"0"
							]
						}
					}
				},
				"seat-view": {
					"UrlTemplate": "{baseUrl}/image/dynamic/MY21_2017/536/seat-view-v1/RB0000/NP02/CB04/_/{profile}.{format}?market=cn&client=vocapp",
					"Resolution": {
						"Width": 4898,
						"Height": 2756
					},
					"UrlTemplateParameters": {
						"profile": {
							"Required": true,
							"Values": [
								"default"
							]
						}
					},
					"QueryParameters": {
						"angle": {
							"Required": false,
							"Values": [
								"0"
							]
						}
					}
				},
				"top-view": {
					"UrlTemplate": "{baseUrl}/image/stateful/MY21_2017/536/top-view-v1/R6/1/70700/RB0000/NC0D/FN02/TP05/CB04/EV02/T21A/LF05/_/CJ07/{profile}.{format}?market=cn&client=vocapp",
					"Resolution": {
						"Width": 4898,
						"Height": 2796
					},
					"UrlTemplateParameters": {
						"profile": {
							"Required": true,
							"Values": [
								"default",
								"basecar",
								"fuelportclosed",
								"fuelportopen",
								"lfdc",
								"rfdc",
								"lbdc",
								"rbdc",
								"lfdo",
								"rfdo",
								"lbdo",
								"rbdo",
								"bdc",
								"bdo",
								"lmcdc",
								"lmodc",
								"lmcdo",
								"lmodo",
								"rmcdc",
								"rmodc",
								"rmcdo",
								"rmodo",
								"roof",
								"cblcharged",
								"cblcharging",
								"cblerror",
								"cblpaused",
								"cblplugged",
								"cblscheduled",
								"aircleaning",
								"aircleaning1",
								"aircleaning2",
								"aircleaning3",
								"aircleaning4",
								"alarmindicator",
								"exteriorlights",
								"interiorlights",
								"cooling1",
								"cooling2",
								"cooling3",
								"cooling4",
								"heating1",
								"heating2",
								"heating3",
								"heating4",
								"unknown1",
								"unknown2",
								"unknown3",
								"unknown4",
								"windowlfdc",
								"windowrfdc",
								"windowlbdc",
								"windowrbdc",
								"windowlfdo",
								"windowrfdo",
								"windowlbdo",
								"windowrbdo",
								"windowroof"
							]
						}
					},
					"QueryParameters": {
						"angle": {
							"Required": false,
							"Values": [
								"0"
							]
						}
					}
				}
			}
		}
	],
	"UrlTemplateParameters": {
		"baseUrl": {
			"Required": true,
			"Values": [
				"https://cas.volvocars.com.cn"
			]
		},
		"format": {
			"Required": true,
			"Values": [
				"jpg",
				"png"
			]
		}
	},
	"QueryParameters": {
		"w": {
			"Required": false,
			"Values": [
				"88",
				"375",
				"435",
				"600",
				"750",
				"768",
				"870",
				"1200",
				"1280",
				"1536",
				"1920",
				"2560",
				"3840",
				"4898"
			]
		},
		"bg": {
			"Required": false,
			"Values": [
				"00000000",
				"ffffff"
			]
		}
	},
	"Errors": []
}
```
{collapsible="true"}

- 根据返回的json体做如下操作
	- 取出Combinations.Views.exterior.UrlTemplate 作为整体的url的template 
	``` java
		{baseUrl}/image/dynamic/MY21_2017/536/exterior-v1/R6/70700/R171/FN02/_/TC06/TP05/_/JT02/GR08/T101/TJ02/TM04/_/CB04/EV02/JB0A/T21A/LF05/_/_/_/_/_/_/_/{profile}.{format}?market=cn&client=vocapp
	```
	- 取出Combinations.UrlTemplateParameters.baseUrl.value[0]替换{baseUrl}
	``` java
		"https://cas.volvocars.com.cn"
	``` 
	- 因为是从inputVin处进入，所以以"Default"替换{profile}
	- 因为是从inputVin处进入，所以以"png"替换{format}
	- 拼接上w=600&bg=00000000
	- 最终得出的url是 [https://cas.volvocars.com.cn/image/dynamic/MY21_2017/536/exterior-v1/R6/70700/R171/FN02/_/TC06/TP05/_/JT02/GR08/T101/TJ02/TM04/_/CB04/EV02/JB0A/T21A/LF05/_/_/_/_/_/_/_/Default.png?market=cn&client=vocapp&w=600&bg=00000000](https://cas.volvocars.com.cn/image/dynamic/MY21_2017/536/exterior-v1/R6/70700/R171/FN02/_/TC06/TP05/_/JT02/GR08/T101/TJ02/TM04/_/CB04/EV02/JB0A/T21A/LF05/_/_/_/_/_/_/_/Default.png?market=cn&client=vocapp&w=600&bg=00000000)

- 获取车辆的基本信息
	- 如果当前rollout了supportsC3VINValidation(参考FeatureFlag.md)
		- 以当前的VIN去检查车辆是否已经被激活 (GetLimitedCarInformationUseCase.kt)
		- GET请求接口获取车辆的基本信息
		```cURL
			curl --request GET \
				 --url https://cepmobtoken.prod.c3.volvocars.com.cn/car-information/car/LYVXEEDE8ML489754 \
				 --header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IlFWVzI2OHJuSlZGdHh2cUs5c214elRwUjlBVV9SUzI1NiIsInBpLmF0bSI6ImYifQ.eyJzY29wZSI6Im9wZW5pZCBlbWFpbCBwcm9maWxlIGNhcmVfYnlfdm9sdm86ZmluYW5jaWFsX2luZm9ybWF0aW9uOmludm9pY2U6cmVhZCBjYXJlX2J5X3ZvbHZvOmZpbmFuY2lhbF9pbmZvcm1hdGlvbjpwYXltZW50X21ldGhvZCBjYXJlX2J5X3ZvbHZvOnN1YnNjcmlwdGlvbjpyZWFkIGN1c3RvbWVyOmF0dHJpYnV0ZXMgY3VzdG9tZXI6YXR0cmlidXRlczp3cml0ZSBvcmRlcjphdHRyaWJ1dGVzIHZlaGljbGU6YXR0cmlidXRlcyB0c3BfY3VzdG9tZXJfYXBpOmFsbCB2b2x2b19vbl9jYWxsOmFsbCIsImNsaWVudF9pZCI6ImNoaW5haWFtIiwiaXNzIjoiaHR0cHM6Ly92b2x2b2lkLmNuLnZvbHZvY2Fycy5jb20iLCJhdWQiOiJhaFA3ZTQiLCJtYXJrZXQiOiJDTiIsImZpcnN0TmFtZSI6IlVua25vd24iLCJsYXN0TmFtZSI6IlVua25vd24iLCJzdWIiOiIzMzYxNzNiNi1lMjIwLTQyNjctYjRmYi1mZTM0MzVkZTc3ZDYiLCJlbWFpbCI6Iis4NjEzODE3MTIwMDQ2IiwiZXhwIjoxNzEwNzQ0NzMyfQ.aNR8tqcA6cERkN1wyNUdqGX4XmKTdtQyqmvq1umzBkn6gUo2LM0yHq-14PIrrTKRW-NSUxMZlszsHZzNpB9CrU-JPNKkc2-ah2G7DS_0L2IiaEHIsYMuHxJwzBgJ_8KHedtVJH-eKW5wfopQORTxeHqtj76F1irdloyiJlkeFBhSSrFydQoOcg1ILlYJaNr8ZtFZKUwft7bsmF9lfk3XH83OaebIqNux0AFr08mFzMi6iXWEZzOMsvIZ9lw2XOptQzmh2myYs3xKCuHp9n1goIRl4vuxUHQ22KMTPDHi5IBrcH4qMk5x-lLn9BXxisfZHxTeVzo4WdQdKyNPyzktcQ' \
				 --header 'User-Agent: vca-android/5.37.0'
		```
		{collapsible="true"}
		返回结果如下
		```json
		{
			"vin": "LYVXEEDE8ML489754",
			"hasOwner": true,
			"hasAnyPairings": true,
			"remoteControlType": "ICUP",
			"accountLinkingType": "SPA_CMA_ANDROID",
			"modelName": "XC40",
			"modelYear": "2021",
			"market": "CN"
		}
		```
		- 成功则可以进行下一步
  	- 如果当前没有rollout supportsC3VINValidation
		- 以当前的VIN去检查车辆是否已经被激活 verifyVinConfigurationUseCase.kt 请求参考
		```cURL
			curl --request GET \
			  --url 'https://gw.consumer.api.volvocars.com/voc/configurations/attributes?clientVersion=voc-android%2F5.37.0&vin=LYVXEEDE8ML489754&client=Android' \
			  --header 'Accept: application/vnd.volvocars.api.voc.attributes.v3+json' \
			  --header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IlFWVzI2OHJuSlZGdHh2cUs5c214elRwUjlBVV9SUzI1NiIsInBpLmF0bSI6ImYifQ.eyJzY29wZSI6Im9wZW5pZCBlbWFpbCBwcm9maWxlIGNhcmVfYnlfdm9sdm86ZmluYW5jaWFsX2luZm9ybWF0aW9uOmludm9pY2U6cmVhZCBjYXJlX2J5X3ZvbHZvOmZpbmFuY2lhbF9pbmZvcm1hdGlvbjpwYXltZW50X21ldGhvZCBjYXJlX2J5X3ZvbHZvOnN1YnNjcmlwdGlvbjpyZWFkIGN1c3RvbWVyOmF0dHJpYnV0ZXMgY3VzdG9tZXI6YXR0cmlidXRlczp3cml0ZSBvcmRlcjphdHRyaWJ1dGVzIHZlaGljbGU6YXR0cmlidXRlcyB0c3BfY3VzdG9tZXJfYXBpOmFsbCB2b2x2b19vbl9jYWxsOmFsbCIsImNsaWVudF9pZCI6ImNoaW5haWFtIiwiaXNzIjoiaHR0cHM6Ly92b2x2b2lkLmNuLnZvbHZvY2Fycy5jb20iLCJhdWQiOiJhaFA3ZTQiLCJtYXJrZXQiOiJDTiIsImZpcnN0TmFtZSI6IlVua25vd24iLCJsYXN0TmFtZSI6IlVua25vd24iLCJzdWIiOiIzMzYxNzNiNi1lMjIwLTQyNjctYjRmYi1mZTM0MzVkZTc3ZDYiLCJlbWFpbCI6Iis4NjEzODE3MTIwMDQ2IiwiZXhwIjoxNzEwNzQ0NzMyfQ.aNR8tqcA6cERkN1wyNUdqGX4XmKTdtQyqmvq1umzBkn6gUo2LM0yHq-14PIrrTKRW-NSUxMZlszsHZzNpB9CrU-JPNKkc2-ah2G7DS_0L2IiaEHIsYMuHxJwzBgJ_8KHedtVJH-eKW5wfopQORTxeHqtj76F1irdloyiJlkeFBhSSrFydQoOcg1ILlYJaNr8ZtFZKUwft7bsmF9lfk3XH83OaebIqNux0AFr08mFzMi6iXWEZzOMsvIZ9lw2XOptQzmh2myYs3xKCuHp9n1goIRl4vuxUHQ22KMTPDHi5IBrcH4qMk5x-lLn9BXxisfZHxTeVzo4WdQdKyNPyzktcQ' \
			  --header 'User-Agent: vca-android/5.37.0' \
			  --header 'VCC-Api-Key: 855fec8628e14ba69b0bd8d6a71af78c' \
			  --data '{
				"client":"Android",
				"clientVersion":"5.37.0"
			}'
		```
		返回结构如下
		```json
			{
				"externalColor": "CRYSTAL WHITE",
				"trimlineEdition": "Standard",
				"modelDescription": "XC40",
				"modelYear": "2021",
				"typeCode": "1811",
				"vin": "LYVXEEDE8ML489754",
				"marketingCode": "CHINA2",
				"serverRegion": "CN",
				"supportsVolvoOnCall": true,
				"supportsRestrictedKey": false,
				"hasElectricalHeaterOnly": true,
				"features": []
			}
		```
		- supportsVolvoOnCall为true 则可进行下一步
	- 保存本地缓存。

- 检查配对情况 
	- 如果存在supportsC3VINValidation
		- 以remoteControlType为判断条件
			- ICUP 跳转icup配对
			- CLASSIC 跳转tsp配对
			- ACCOUNT_LINKING (未知)
			- NONE
			- HUANFU
	- 如果不存在supportsC3VINValidation
		- 先检查车辆的配对状况
		```cURL
			curl --request GET \
			  --url https://gw.consumer.api.volvocars.com/voc/configurations/pairinginformation/LYVXEEDE8ML489754 \
			  --header 'Accept: application/vnd.volvocars.api.voc.pairinginformation.v3+json' \
			  --header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsImtpZCI6IlFWVzI2OHJuSlZGdHh2cUs5c214elRwUjlBVV9SUzI1NiIsInBpLmF0bSI6ImYifQ.eyJzY29wZSI6Im9wZW5pZCBlbWFpbCBwcm9maWxlIGNhcmVfYnlfdm9sdm86ZmluYW5jaWFsX2luZm9ybWF0aW9uOmludm9pY2U6cmVhZCBjYXJlX2J5X3ZvbHZvOmZpbmFuY2lhbF9pbmZvcm1hdGlvbjpwYXltZW50X21ldGhvZCBjYXJlX2J5X3ZvbHZvOnN1YnNjcmlwdGlvbjpyZWFkIGN1c3RvbWVyOmF0dHJpYnV0ZXMgY3VzdG9tZXI6YXR0cmlidXRlczp3cml0ZSBvcmRlcjphdHRyaWJ1dGVzIHZlaGljbGU6YXR0cmlidXRlcyB0c3BfY3VzdG9tZXJfYXBpOmFsbCB2b2x2b19vbl9jYWxsOmFsbCIsImNsaWVudF9pZCI6ImNoaW5haWFtIiwiaXNzIjoiaHR0cHM6Ly92b2x2b2lkLmNuLnZvbHZvY2Fycy5jb20iLCJhdWQiOiJhaFA3ZTQiLCJtYXJrZXQiOiJDTiIsImZpcnN0TmFtZSI6IlVua25vd24iLCJsYXN0TmFtZSI6IlVua25vd24iLCJzdWIiOiI2YmY3NTEzMy00OGYxLTRjZWMtOTk1Yi1mNWE3NGZmYzM1YTQiLCJlbWFpbCI6Iis4NjE4NjE2OTUzNTQwIiwiZXhwIjoxNzEwNzUxODg1fQ.eOHTH2iA7488Htm3zY_NKFRKbbCyxf_a7KNK99vKVfCnVGjE3A_TTUfx1VuyZ0lqy_6vGIfaoFyT6JKxivqHLJdoD8f0tLmhZSNUstPcP_6Hfj3LViYBrvGyPkE2Vbn3LQjCcbXtBYDBJnSKuL57ipaYPxtUVdfMdqfvfrFT3rorG90CNypDhf3Jqo3jUJMIiH_24a5-Jc6haN1qy9UwONQHnAKKFXmuCdqWdqBqicvArPieAkfteTXRo4kUT2hF0lv4eCQYR03zcK9Ld7J9UlRdM1ssS3tVgWZjTgQ6GFIjja0_ZyLy2TI4MOx86Q_ETPXo_5gt79-XuU4IdABVpg' \
			  --header 'User-Agent: vca-android/5.37.0' \
			  --header 'VCC-Api-Key: 855fec8628e14ba69b0bd8d6a71af78c'
		```
		返回结果如下
		```json
		{
			"infotainmentHeadUnitType": "SPA",
			"pairingSupported": true,
			"vin": "LYVXEEDE8ML489754"
		}
		```
	- 根据infotainmentHeadUnitType 和 pairingSupported 来判断
		- 如果根据infotainmentHeadUnitType为icup并且pairingSupported为true则跳转icup配对
		- 如果根据infotainmentHeadUnitType为icup并且pairingSupported为false则返回错误，不支持配对
		- 如果根据infotainmentHeadUnitType为其他则跳转tsp配对
