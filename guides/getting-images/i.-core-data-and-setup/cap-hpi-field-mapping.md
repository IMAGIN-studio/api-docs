# 🎯 CAP HPI field mapping

## CAP HPI Integration: Field Mapping Guide

This guide details how to leverage CAP HPI unique identifiers to request vehicle images from the IMAGIN.studio CDN. Using CAP HPI data simplifies your integration by allowing you to specify a vehicle using its ID instead of multiple individual data points.

***

### 1. How to Use CAP HPI Identifiers

By providing the required CAP HPI parameters, the IMAGIN.studio CDN can instantly map to the corresponding vehicle in our catalog and deliver the image.

#### Core Request Structure

When using CAP HPI, the required `make` and `modelFamily` parameters are replaced by the unique CAP HPI identifiers.

| **Parameter**                                                | **Type** | **Required** | **Description**                                                        | **Example Value**   |
| ------------------------------------------------------------ | -------- | ------------ | ---------------------------------------------------------------------- | ------------------- |
| <mark style="background-color:$primary;">customer</mark>     | String   | Yes          | Your unique API Customer Key.                                          | `{yourcustomerkey}` |
| <mark style="background-color:purple;">capVehicleType</mark> | String   | Yes          | The vehicle category as defined by CAP HPI.                            | `car` or `lcv`      |
| <mark style="background-color:yellow;">capId</mark>          | String   | Yes          | The unique identifier assigned by CAP HPI to the specific vehicle/LCV. | `96578`             |

#### Example: Basic CAP HPI Request

This request uses the unique `capId` to fetch the image for the specified vehicle type.

https://cdn.imagin.studio/getImage?<mark style="background-color:orange;">customer={yourcustomerkey}</mark><mark style="background-color:purple;">\&capVehicleType=car</mark><mark style="background-color:yellow;">\&capId=96578</mark>

***

### 2. Optional Image Refinement Parameters

You can combine the CAP HPI identifiers with various optional parameters to control the visual output, such as angle, zoom, and resolution.

| **Parameter**           | **Description**                                                                                  | **Possible Values**                                                                                | **Example Value**    |
| ----------------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- | -------------------- |
| `angle`                 | Specifies the camera viewing angle (e.g., side profile, three-quarter view).                     | Refer to our [Selecting Angles](../ii.-image-customization-and-styling/selecting-angles.md) guide. | `23`                 |
| `zoomType`              | Controls how the vehicle fits onto the canvas.                                                   | `relative`, `fullscreen`,`adaptive`                                                                | `fullscreen`         |
| `zoomLevel`             | Controls the magnification of the vehicle on the canvas (0-30).                                  | `0` to `30`                                                                                        | `15`                 |
| `width`                 | The desired image width in pixels. The CDN resolves this to the nearest available standard size. | `400`, `800`, `1200`, `1600`, etc.                                                                 | `800`                |
| `fileType`              | The output image format. Defaults to `webp`.                                                     | `png`, `jpg`, `webp`                                                                               | `png`                |
| `groundPlaneAdjustment` | Fine-tunes the vertical position of the car on the ground plane (decimal percentage).            | `-1` to `1`                                                                                        | `-0.07`              |
| `billingTag`            | Optional identifier for associating the API call with a specific business unit.                  | Any string (e.g., `showroom`, `website_v2`)                                                        | `showroom`           |
| `tailoring`             | Your tailoring key, used to control the custom branding (e.g., license plate logo).              | Varies by customer setup.                                                                          | `my-dealership-logo` |

#### Example: Refined CAP HPI Request

This request fetches the image identified by the `capId`, but overrides the default angle and zoom settings for a custom display.

https://cdn.imagin.studio/getImage?<mark style="background-color:orange;">customer={yourcustomerkey}</mark><mark style="background-color:purple;">\&capVehicleType=car</mark><mark style="background-color:yellow;">\&capId=96578</mark><mark style="background-color:green;">\&angle=23</mark><mark style="background-color:red;">\&zoomType=relative</mark><mark style="background-color:blue;">\&width=1600</mark>
