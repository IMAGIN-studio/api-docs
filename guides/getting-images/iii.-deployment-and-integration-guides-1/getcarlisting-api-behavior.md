# 📋 getCarListing

## API Reference: `getCarListing`

This endpoint allows developers to query our visual catalog structure. It is designed to act as the pipeline for your internal dashboards, back-office tooling, and user-facing inventory widgets.

By utilizing `getcarlisting`, you can retrieve the exact parameters, IDs, and configurations needed to dynamically render and display high-quality vehicle assets via the IMAGIN.studio API.

⚠️ **Please Note:** _This endpoint is a catalog exploration and image-integration utility. IMAGIN.studio is a visual content suite, not a standalone data provider; this API is not intended for raw data harvesting or general automotive dataset distribution._

***

### 1. How the API Works: Filtering Down Data

The `getCarListing` API allows for progressive data discovery. You start with basic parameters and the response provides the next layer of available information, enabling you to build dynamic selection menus or validate data points within your system.

#### API Endpoint URL

<mark style="background-color:green;">https://cdn.imagin.studio/getCarListing?</mark><mark style="background-color:yellow;">\&customer={yourcustomerkey}</mark>

| **Parameter**                                          | **Type** | **Description**           |
| ------------------------------------------------------ | -------- | ------------------------- |
| <mark style="background-color:yellow;">customer</mark> | String   | Your unique customer key. |

#### Filtering Logic

To filter, you add known parameters to the request. The API responds with a list of the _next_ available data points based on the constraints you've provided.

| **Parameters Provided** | **Next Layer of Data Returned**                      |
| ----------------------- | ---------------------------------------------------- |
| None (just `customer`)  | A list of available makes (manufacturers).           |
| `make=BMW`              | A list of available modelFamilies for that make.     |
| `modelFamily=3-series`  | A list of available modelRanges, modelVariants, etc. |

***

### 2. Technical Implementation and Response Format

The API returns a JSON object. The key of the JSON object indicates the parameter type being returned (e.g., `make`), and the value is an array of strings containing the available data points.

#### JavaScript Helper Function

The following helper demonstrates how to call the API and process its structured response:

JavaScript

{% code overflow="wrap" lineNumbers="true" %}
```javascript
// URL of the JSON data
const baseURL = `https://cdn.imagin.studio/getCarListing`;

/**
 * Fetches available car data points based on provided constraints.
 * @param {Array<string>} parameters - An array of query string parameters (e.g., ["customer=test", "make=bmw"]).
 * @returns {Promise<{parameter: string, data: Array<string>}>} - The returned data, structured with the parameter key and data array.
 */
const getCarListing = async (parameters) => {
  return fetch(`${baseURL}?${parameters.join("&")}`)
    .then(response => {
      if (!response.ok) throw new Error('Network response was not ok');
      return response.json();
    })
    .then(data => {
      // The API returns a single-key object, e.g., { "make": ["audi", "bmw", ...] }
      const key = Object.keys(data)[0]; 
      return { 
        parameter: key, // e.g., "make"
        data: data[key] // e.g., ["audi", "bmw", ...]
      };
    })
    .catch(error => console.error('Error fetching car listing:', error));
}

// Example Request 1: Get all available makes
const result = await getCarListing(["customer=<your customer key>"]); 
// Response will be: { parameter: "make", data: ["audi", "bmw", "toyota", ...] }

// Example Request 2: Filter to available modelFamilies for BMW
const bmwModels = await getCarListing(["customer=<your customer key>", "make=bmw"]);
// Response will be: { parameter: "modelFamily", data: ["1-series", "3-series", "x5", ...] }
```
{% endcode %}

