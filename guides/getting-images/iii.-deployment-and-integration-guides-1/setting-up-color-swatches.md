# 🖌️ getPaints

## `getPaints`

This endpoint returns the valid paint codes available for a given make/vehicle in the IMAGIN.studio catalog.&#x20;

Use `getpaints` to dynamically populate color-selection dropdowns and ensure that the color parameters requested in your rendering pipeline match valid catalog options.

⚠️ **Please Note:** _This endpoint is an asset-configuration utility designed to facilitate image rendering. IMAGIN.studio is a visual content suite, not a standalone automotive data provider; this API is not intended to be used as a general paint-database reference. For retrieving the digital paint swatch image assets, please use the dedicated `getpaintswatches` endpoint._

***

### 1. API Endpoint: `getPaints`

Retrieve valid paint color codes and names to drive interactive vehicle configurators and visual dashboards.

#### API Endpoint URL

<mark style="background-color:green;">https://cdn.imagin.studio/getPaints?</mark><mark style="background-color:yellow;">\&customer={yourcustomerkey}</mark><mark style="background-color:$info;">\&target=make</mark><mark style="background-color:violet;">\&make=bmw</mark>

#### Required Parameters

| **Parameter**                                          | **Type** | **Description**                          |
| ------------------------------------------------------ | -------- | ---------------------------------------- |
| <mark style="background-color:yellow;">customer</mark> | String   | Your unique customer key.                |
| <mark style="background-color:$info;">target</mark>    | Constant | The target of the paint search.          |
| <mark style="background-color:violet;">make</mark>     | String   | The vehicle manufacturer (e.g., `bmw`).  |
|                                                        |          |                                          |

#### Example Request

This request fetches the swatch data for a specific paint color, utilizing the vehicle context for accuracy:

https://cdn.imagin.studio/getPaints?<mark style="background-color:yellow;">customer={yourcustomerkey}</mark><mark style="background-color:$info;">\&target=make</mark><mark style="background-color:violet;">\&make=bmw</mark>

***

### 3. Response Structure (JSON)

The API returns a JSON array containing objects for each requested make. &#x20;

#### Example JSON Response Snippet

```
                {
                    "paintData": {
                        "target": "car",
                        "make": "audi",
                        "modelFamily": "a1",
                        "modelRange": "0",
                        "modelVariant": "0",
                        "bodySize": null,
                        "modelYear": "2022",
                        "trim": "eu",
                        "powerTrain": null,
                        "paintCombinations": {
                            "pspc0101": {
                                "mapped": {
                                    "2ypa": {
                                        "paintDescription": "glacier-white-metallic",
                                        "nativePaintDescriptions": [],
                                        "orderable": true,
                                        "available": true
                                    }
                                },
                                "paintSwatch": {
                                    "primary": {
                                        "highLight": "#abacb1",
                                        "lowLight": "#aeaead"
                                    }
                                }
                            }
                        }
                    }
                }
```
