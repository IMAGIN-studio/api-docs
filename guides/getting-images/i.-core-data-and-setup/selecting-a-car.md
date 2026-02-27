# 🚘 Selecting a Car

## Vehicle Selection Guide: Getting Images

This guide details how to select the exact vehicle for your image request using the IMAGIN.studio getImage API. Providing accurate data points ensures immediate, high-quality image delivery and fuels our machine learning system for continuous improvement.

***

### 1. The Essentials: Required Parameters

To fetch any image, your request must contain the following three core data points. These parameters should be added to the URL request.

| **Parameter**                                             | **Type** | **Description**           | **Example Value**   |
| --------------------------------------------------------- | -------- | ------------------------- | ------------------- |
| <mark style="background-color:yellow;">customer</mark>    | String   | Your unique customer key. | `{yourcustomerkey}` |
| <mark style="background-color:blue;">make</mark>          | String   | The vehicle manufacturer  | `toyota`            |
| <mark style="background-color:orange;">modelFamily</mark> | String   | The base model name       | `corolla`           |

#### Minimum Request Example

https://cdn.imagin.studio/getImage?<mark style="background-color:yellow;">customer={yourcustomerkey}</mark><mark style="background-color:blue;">\&make=toyota</mark><mark style="background-color:orange;">\&modelFamily=corolla</mark>

***

### 2. Refining Your Vehicle Specification

For precise results—down to the exact trim, body style, and engine—you can add optional parameters. The more data you provide, the closer we match the image to your exact inventory.

#### Key Optional Data Points

| **Parameter**                                         | **Description**                                                                                                                             |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">modelRange</mark>          | The specific model range or sub-model (e.g., `corolla-gr`).                                                                                 |
| <mark style="color:blue;">modelVariant</mark>         | A variant code or body style (e.g. hatchback and panel van).                                                                                |
| <mark style="color:purple;">modelYear</mark>          | The model production year (e.g., `2023`).                                                                                                   |
| <mark style="color:orange;">powerTrain</mark>         | The engine type (e.g., `petrol`, `hybrid`, `electric`).                                                                                     |
| <mark style="color:$danger;">paintDescription</mark>  | The human-readable name associated with the paint color. This can be the OEM color name or an equivalent identifier (e.g. `vermillion-red`) |
| <mark style="color:yellow;">paintid</mark>            | The unique ID for the car's exterior paint color (e.g., `11272`).                                                                           |
| <mark style="color:$info;">angle</mark>               | The viewing angle for the image (default is `01`).                                                                                          |
| <mark style="color:red;">zoomtype</mark>              | The camera zoom/frame setting (e.g., `fullscreen`).                                                                                         |

***

#### Specific Request Example

This request specifies a 2023 Corolla GR Hatchback in a custom paint color and a specific angle, overriding all default values.

https://cdn.imagin.studio/getImage?customer={yourcustomerkey}\&make=toyota\&modelFamily=corolla<mark style="color:green;">\&modelRange=corolla-gr</mark><mark style="color:blue;">\&modelVariant=ha</mark><mark style="color:purple;">\&modelYear=2023</mark><mark style="color:orange;">\&powerTrain=petrol</mark><mark style="color:$info;">\&angle=23</mark><mark style="color:yellow;">\&paintid=11272</mark><mark style="color:$danger;">\&paintDescription=vermillion-red</mark><mark style="color:red;">\&zoomtype=fullscreen</mark>

***

### 3. Intelligent Fallback and Defaults

Our CDN is designed to always return an image, even when data is incomplete. This is achieved through defined defaults and a dynamic assumption system.

#### Prioritize Specificity

When you omit a parameter from the API request, the CDN must make an assumption to fulfill the request. To guarantee you receive the exact image you require, we strongly recommend providing as much specificity as possible.

The only assumption our system makes explicitly is regarding the model's age:

| **Default Vehicle Parameter** | **Value**                                                                                                      |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `modelYear`                   | If omitted, the system defaults to the latest available model year for the requested `make` and `modelFamily`. |

#### Handling Data Mismatches and Inaccuracy

If your data doesn't perfectly match our catalog (e.g., providing `make=vw` instead of `make=volkswagen`), our CDN uses machine learning to:

1. Find the Closest Match: We deliver the closest available image based on the data provided.
2. Learn and Adapt: Our system learns from the request and continues to analyze your provided data.
3. Automatic Update: If the system later identifies a better, more accurate image match based on this learning, the image returned via the same URL will automatically update without requiring any change to your code.

In the rare event that provided data is highly inaccurate or for an extremely uncommon model, a generic placeholder image may be returned.&#x20;

***

#### Best Practice for Data Fields

To maintain system integrity and accuracy, do not use descriptive values like `default`, `unknown`, or similar for any parameter.

Instead, simply omit the attribute from the request URL entirely, or leave its value empty if passing it through a system that requires the key:

| **❌ Avoid**             | **✅ Use This Approach** |
| ----------------------- | ----------------------- |
| `&powerTrain=unknown`   | Omit the parameter      |
| `&modelVariant=default` |                         |
