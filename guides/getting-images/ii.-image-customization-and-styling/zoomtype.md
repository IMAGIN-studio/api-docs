# 🔍 zoomType

## zoomType: Controlling Vehicle Framing

The `zoomType` parameter is essential for controlling how the vehicle is scaled and framed within the output image canvas. Selecting the correct type ensures visual consistency across your platform, regardless of the vehicle's actual size or the angle being viewed.

### Parameter Usage

| **Parameter Name** | **Available Values**                 | **Default Value**              |
| ------------------ | ------------------------------------ | ------------------------------ |
| `zoomType`         | `relative`, `adaptive`, `fullscreen` | e.g., `adaptive` for 360° view |

You include the desired value in your `getImage` request: `...&zoomType=relative`.

### Zoom Type Breakdown

#### 1. `relative` (Consistent Sizing for Listings)

The `relative` zoom type ensures that all vehicle images maintain a consistent, proportionate size relative to each other, regardless of the individual model's actual physical dimensions.

| **Use Case**           | **Description**                                                                                                                                   |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Vehicle Overview Pages | Ideal for side-by-side displays (e.g., search results or comparison tools), guaranteeing a uniform appearance and layout across different models. |
| Catalog Listings       | Maintains consistent image sizing across a product catalog, contributing to a clean, organized, and professional layout.                          |

#### 2. `adaptive` (Consistent Sizing for 360° Spinners)

The `adaptive` zoom type intelligently maximizes the vehicle's size within the available display space while dynamically preserving its natural proportions across all viewing angles. This is the standard setting for interactive experiences.

| **Use Case**     | **Description**                                                                                                                                     |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| 360° Spinners    | This is the default for 360° views (`angle=200` to `angle=231`), ensuring the vehicle appears consistently sized and smooth as the user rotates it. |
| Dynamic Displays | Perfect when your layout needs to adjust image sizes based on available screen space while always maintaining the car's proportional view.          |

#### 3. `fullscreen` (Maximum Visual Impact)

The `fullscreen` zoom type maximizes the vehicle image to fill the entire available canvas, prioritizing the vehicle's visual presence and detail over consistent sizing with other elements.

| **Use Case**           | **Description**                                                                                                              |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Detailed Product Pages | Allows users to appreciate the car's features and design with maximum clarity and impact on individual vehicle detail pages. |
| Hero Images & Banners  | Recommended when you need the vehicle to dominate the visual space and create an immediate, striking impression.             |

By understanding these distinctions, you can select the `zoomType` that best aligns with your design goals and enhances the user's experience on your platform.

### \&zoomType=relative

<div align="center"><figure><img src="https://cdn-08.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=smart&#x26;modelFamily=fortwo&#x26;modelRange=fortwo&#x26;angle=05&#x26;zoomtype=relative" alt="" width="563"><figcaption></figcaption></figure></div>

<div align="center"><figure><img src="https://cdn-08.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=ford&#x26;modelFamily=f-250&#x26;modelRange=f-250-super-duty&#x26;angle=05&#x26;zoomtype=relative" alt="" width="563"><figcaption></figcaption></figure></div>

### \&zoomType=fullscreen



<figure><img src="https://cdn-08.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=smart&#x26;modelFamily=fortwo&#x26;modelRange=fortwo&#x26;angle=05&#x26;zoomtype=fullscreen" alt=""><figcaption></figcaption></figure>

<figure><img src="https://cdn-08.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=ford&#x26;modelFamily=f-250&#x26;modelRange=f-250-super-duty&#x26;angle=05&#x26;zoomtype=fullscreen" alt=""><figcaption></figcaption></figure>

### \&zoomType=adaptive

<figure><img src="https://cdn.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=bmw&#x26;modelFamily=3&#x26;modelVariant=ca&#x26;modelYear=2021&#x26;modelrange=m3&#x26;transmission=0&#x26;bodySize=2&#x26;trim=m3&#x26;paintId=imagin-grey&#x26;angle=208" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="https://cdn.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=bmw&#x26;modelFamily=3&#x26;modelVariant=ca&#x26;modelYear=2021&#x26;modelrange=m3&#x26;transmission=0&#x26;bodySize=2&#x26;trim=m3&#x26;paintId=imagin-grey&#x26;angle=200" alt="" width="563"><figcaption></figcaption></figure>
