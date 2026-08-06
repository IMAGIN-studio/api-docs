# 🎨 getPaintSwatches

## API Reference: `getPaintSwatches`

This guide details how to use the `getPaintSwatches` API to retrieve the necessary color information for dynamically generating paint tiles or color swatches within your application.

Providing paint data is key to ensuring seamless mapping and high-quality image delivery, as paint availability can be complex, varying by car model, market, and product codes.

***

### 1. API Endpoint: `getPaintSwatches`

The `getPaintSwatches` API allows you to retrieve the color information based on the paint IDs you provide. This data is essential for rendering accurate color swatches on your product pages.

#### API Endpoint URL

<mark style="background-color:green;">https://cdn.imagin.studio/getPaintSwatches?</mark><mark style="background-color:yellow;">\&customer={yourcustomerkey}</mark>

#### Required Parameters

| **Parameter**                                          | **Type** | **Description**                                                                                                                   |
| ------------------------------------------------------ | -------- | --------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="background-color:yellow;">customer</mark> | String   | Your unique customer key.                                                                                                         |
| <mark style="background-color:purple;">paints</mark>   | String   | The specific Paint ID you want information for. (Must be a value already mapped in our system).                                   |
| <mark style="background-color:blue;">make</mark>       | String   | The vehicle manufacturer (e.g., `bmw`). Highly recommended to distinguish between identical paint codes used by different brands. |

#### Optional Parameter&#x20;

Providing vehicle context is recommended because many paint codes are not unique across different manufacturers or model lines. Including this parameter ensures you retrieve the correct swatch data.

| **Parameter**                                          | **Type** | **Description**                                                                               |
| ------------------------------------------------------ | -------- | --------------------------------------------------------------------------------------------- |
| <mark style="background-color:red;">modelFamily</mark> | String   | The vehicle model family (e.g., `x5`). Recommended to provide specific context for the paint. |

#### Example Request

This request fetches the swatch data for a specific paint color, utilizing the vehicle context for accuracy:

https://cdn.imagin.studio/getPaintSwatches?<mark style="background-color:yellow;">customer={yourcustomerkey}</mark><mark style="background-color:blue;">\&make=bmw</mark><mark style="background-color:red;">\&modelFamily=x5</mark><mark style="background-color:purple;">\&paints=376</mark>

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
