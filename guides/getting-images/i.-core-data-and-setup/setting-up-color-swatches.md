# 🎨 Setting Up Color Swatches

## API Reference: `getPaintSwatches`

This guide details how to use the `getPaintSwatches` API to retrieve the necessary color information for dynamically generating paint tiles or color swatches within your application.

Providing paint data is key to ensuring seamless mapping and high-quality image delivery, as paint availability can be complex, varying by car model, market, and product codes.

***

### 1. Understanding Paint Data Complexity

Car paint data is complex due to various factors. The `getPaintSwatches` API helps abstract this complexity by providing the normalized data you need:

* Regional Differences: A paint may be available in one country but not another.
* Multiple Codes: The same color can be known by numerous product codes.
* Model Specificity: A paint might be exclusive to specific vehicle models or trims.
* Code Collisions: In rare cases, the same paint code might be used for two distinct colors by the same manufacturer in different markets.

Recommendation: We highly recommend maintaining a record of the specific paint IDs you use across your channels. We use these IDs to map to our unique color identifiers, which we call the (spray can) identifiers.

***

### 2. API Endpoint: `getPaintSwatches`

The `getPaintSwatches` API allows you to retrieve the color information based on the paint IDs you provide. This data is essential for rendering accurate color swatches on your product pages.

#### API Endpoint URL

<mark style="background-color:green;">https://cdn.imagin.studio/getPaintSwatches?</mark><mark style="background-color:yellow;">\&customer={yourcustomerkey}</mark>

#### Required Parameters

| **Parameter**                                          | **Type** | **Description**                                                                                 |
| ------------------------------------------------------ | -------- | ----------------------------------------------------------------------------------------------- |
| <mark style="background-color:yellow;">customer</mark> | String   | Your unique customer key.                                                                       |
| <mark style="background-color:purple;">paintId</mark>  | String   | The specific Paint ID you want information for. (Must be a value already mapped in our system). |

#### Optional Parameters&#x20;

Providing vehicle context is recommended because many paint codes are not unique across different manufacturers or model lines. Including these parameters ensures you retrieve the correct swatch data.

| **Parameter**                                          | **Type** | **Description**                                                                                                                   |
| ------------------------------------------------------ | -------- | --------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="background-color:blue;">make</mark>       | String   | The vehicle manufacturer (e.g., `bmw`). Highly recommended to distinguish between identical paint codes used by different brands. |
| <mark style="background-color:red;">modelFamily</mark> | String   | The vehicle model family (e.g., `x5`). Recommended to provide specific context for the paint.                                     |

#### Example Request

This request fetches the swatch data for a specific paint color, utilizing the vehicle context for accuracy:

https://cdn.imagin.studio/getPaintSwatches?<mark style="background-color:yellow;">customer={yourcustomerkey}</mark><mark style="background-color:blue;">\&make=bmw</mark><mark style="background-color:red;">\&modelFamily=x5</mark><mark style="background-color:purple;">\&paintId=11272</mark>

***

### 3. Response Structure (JSON)

The API returns a JSON array containing objects for each requested `paintId`.  A typical response provides the unique color identifier, the name, and the color values needed for rendering.

| **Field**     | **Type** | **Description**                                                                                                      | **Example Value**                                |
| ------------- | -------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| `paintId`     | String   | The unique identifier you provided in the request.                                                                   | `imagin-red`                                     |
| `description` | String   | The human-readable name associated with the paint color. This can be the OEM color name or an equivalent identifier. | `Volcano Red Metallic`                           |
| `hexValue`    | String   | The hexadecimal color code for the swatch background.                                                                | `#CC0000`                                        |
| `sprayCanId`  | String   | The unique internal identifier for the actual paint color.                                                           | `XYZ-12345`                                      |
| `imageURL`    | String   | (Optional) URL to an image file if the swatch is a complex texture.                                                  | `https://cdn.imagin.studio/swatch/XYZ-12345.png` |

#### Example JSON Response Snippet

JSON

{% code overflow="wrap" lineNumbers="true" %}
```json
[
  {
    "paintId": "imagin-red",
    "description": "Volcano Red Metallic",
    "hexValue": "#CC0000",
    "sprayCanId": "XYZ-12345",
    "imageURL": null
  },
  {
    "paintId": "sky-blue",
    "description": "Azure Sky Pearl",
    "hexValue": "#007FFF",
    "sprayCanId": "ABC-67890",
    "imageURL": "https://cdn.imagin.studio/swatch/ABC-67890.png" 
  }
]
```
{% endcode %}
