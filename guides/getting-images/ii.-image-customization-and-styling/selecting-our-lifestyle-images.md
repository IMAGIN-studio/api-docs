---
description: >-
  Discover a world of possibilities for your car photos with our expertly
  curated lifestyle surroundings.
---

# 🌇 Selecting Our Lifestyle Images

## Selecting Our Lifestyle Images: Contextualizing Your Vehicles <a href="#selecting-our-lifestyle-images-contextualizing-your-vehicles" id="selecting-our-lifestyle-images-contextualizing-your-vehicles"></a>

Placing your vehicles in aspirational, real-world settings can significantly enhance the customer experience and drive conversion rates. This guide details the four parameters needed to select and customize a lifestyle background.&#x20;

***

#### The Lifestyle Parameters

To trigger a lifestyle delivery, you must include the `surrounding` data point in your base `getImage` request. All other data points are optional features used to fine-tune your creative vision.

| **Parameter**        | **Purpose**                                                     | **Example Values**                                 |
| -------------------- | --------------------------------------------------------------- | -------------------------------------------------- |
| **`surrounding`**    | **Chooses the base setting from our library.**                  | **`sur33` (Italian Street), `sur34` (White Hall)** |
| `angle`              | Selects the specific camera perspective (Replaces _viewPoint_). | `angle=1`, `angle=23`                              |
| `aspectRatio`        | Optimizes dimensions for your target platform.                  | `16:10`, `10:16`, `2:1`, `32:9`                    |
| `wideScreenPosition` | Controls vehicle horizontal offset (Replaces _overlayArea_).    | `none`, `left`, `right`                            |
| `zoomType`           | Crops the scene to make the vehicle "Full Screen."              | `fullscreen`                                       |

***

#### Detailed Parameter Breakdown

**1. surrounding (The Scene)**

Choose from a growing library of expertly curated, picturesque backgrounds.

* **New Default:** We have set Surrounding 34 (White Hall 2.0) as the new default. If you request a lifestyle image that hasn't been rendered yet, you will instantly receive the vehicle in this minimalist environment while your specific request processes.

**2. angle (The Perspective)**

To simplify your requests, we have replaced "viewPoint" with angle. We have also significantly increased your creative control:

* **Expanded Options:** Each surrounding now offers up to 13 distinct angles (increased from the previous 5–8).
* **Consistency:** Use the `angle` parameter (e.g., `angle=5`) to define all camera positions.

**3. aspectRatio (The Dimensions)**

Ensure your image is optimized for the intended display size. Our versatile collection supports:

* 16:10: Widescreen
* 10:16: Vertical Mobile
* 2:1: Panoramic
* 32:9: Ultra-widescreen

**4. wideScreenPosition (Vehicle Positioning)**

Formerly known as _overlayArea_, wideScreenPosition allows you to precisely offset the car to accommodate text or UI elements.

* Options: `none` (centered), `left`, `right`.

**5. zoomType (The Framing)**

By adding `zoomType=fullscreen`, you can modify the camera focus. This crops out a portion of the lifestyle background to ensure the vehicle is front and center, taking up most of the image for a high-impact, full-screen effect.

#### **The Datapoints**

You must provide the following three datapoints in your API request to generate a lifestyle image:

* <mark style="background-color:red;">Permission piece to access IMAGIN.studio CDN</mark> <mark style="color:$danger;background-color:red;">(Required!)</mark>
* <mark style="background-color:green;">Basic studio image request</mark> <mark style="color:$danger;background-color:green;">(Required!)</mark>
* <mark style="background-color:blue;">Surrounding</mark> <mark style="color:$danger;background-color:blue;">(Required!)</mark><mark style="background-color:blue;">:</mark> This datapoint specifies the environment in which the vehicle is placed. Each surrounding is represented by a unique ID (e.g., sur33).
* <mark style="background-color:purple;">Angle:</mark> This datapoint defines the specific camera angle of the vehicle. This replaces the legacy viewpoint datapoint. Each angle is represented by a unique ID (e.g., 5).
* <mark style="background-color:yellow;">aspect Ratio:</mark> This datapoint determines the width and height proportion of the final image (e.g., 32:9).
* <mark style="background-color:orange;">widescreenPosition:</mark> This datapoint determines if the vehicle is in the centre of the page (none), to the left or right&#x20;

**Example Request URL**

The following URL demonstrates a basic request for a BMW X1 lifestyle image. You can use it as a template, replacing the datapoint values with your desired options.&#x20;

<mark style="background-color:red;">https://cdn.imagin.studio/getImage?\&customer={YourCustomerKey}</mark><mark style="background-color:green;">\&make=audi\&modelFamily=a5\&paintId=imagin-red\&width=1200</mark><mark style="background-color:blue;">\&surrounding=sur33</mark><mark style="background-color:purple;">\&angle=1</mark><mark style="background-color:yellow;">\&aspectRatio=32:9</mark><mark style="background-color:orange;">\&widescreenPosition=right</mark><br>

### Lifestyle Surroundings <a href="#lifestyle-surroundings" id="lifestyle-surroundings"></a>

<figure><img src="../../../.gitbook/assets/v2italianstree.webp" alt=""><figcaption><p>Surrounding 33 (Italian Street Sunset)</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v2whitehall.webp" alt=""><figcaption><p>Surrounding 34 (White Hall; Default Surrounding) </p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v2sunsethouse.webp" alt=""><figcaption><p>Surrounding 35 (Sunset House)</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/silver.webp" alt=""><figcaption><p>Surrounding 38 (Tundra Road)</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v2euro.webp" alt=""><figcaption><p>Surrounding 39 (Dutch Terraced House)</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v2warehouse.webp" alt=""><figcaption><p>Surrounding 44 (Warehouse)</p></figcaption></figure>

### Angles  <a href="#lifestyle-surroundings" id="lifestyle-surroundings"></a>

<figure><img src="../../../.gitbook/assets/v21.webp" alt=""><figcaption><p>angle 01</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v25.webp" alt=""><figcaption><p>angle 05</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v29.webp" alt=""><figcaption><p>angle 09</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v213.webp" alt=""><figcaption><p>angle 13</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v217.webp" alt=""><figcaption><p>angle 17</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v222.webp" alt=""><figcaption><p>angle 21</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/V2223.webp" alt=""><figcaption><p>angle 22</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v223.webp" alt=""><figcaption><p>angle 23</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v225.webp" alt=""><figcaption><p>angle 25</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v228.webp" alt=""><figcaption><p>angle 27</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v227.webp" alt=""><figcaption><p>angle 28</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/v29.webp" alt=""><figcaption><p>angle 29</p></figcaption></figure>

<figure><img src="/broken/files/oWyz0jpgolnNDsgIS9P1" alt=""><figcaption><p>angle 33</p></figcaption></figure>

### Aspect Ratio

<figure><img src="../../../.gitbook/assets/angle16.webp" alt=""><figcaption><p>16:10</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/angle1016.webp" alt=""><figcaption><p>10:16</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/angletwo1.webp" alt=""><figcaption><p>2:1</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/angle329.webp" alt=""><figcaption><p>32:9</p></figcaption></figure>

### Wide Screen Position

<figure><img src="../../../.gitbook/assets/none.webp" alt=""><figcaption><p>none</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/left.webp" alt=""><figcaption><p>left</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/right.webp" alt=""><figcaption><p>right</p></figcaption></figure>

### **Zoom Type Fullscreen**&#x20;

<figure><img src="../../../.gitbook/assets/1111111.webp" alt=""><figcaption><p>no fullscreen</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/getImage (14).webp" alt=""><figcaption><p>fullscreen applied</p></figcaption></figure>
