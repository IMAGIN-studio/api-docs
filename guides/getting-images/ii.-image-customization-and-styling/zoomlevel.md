# 🔍 zoomLevel

## zoomLevel: Fine-Tuning Vehicle Magnification

The `zoomLevel` parameter allows you to manually adjust the vehicle's size on the canvas for purposes such as fine-tuning the composition or achieving a slightly wider perspective.

### Parameter Usage and Values

| **Parameter Name** | **Value Range**            | **Default Value**    |
| ------------------ | -------------------------- | -------------------- |
| `zoomLevel`        | Numerical (e.g., 0 to 100) | Varies by `zoomType` |

You include the numerical level in your `getImage` request: `...&zoomLevel=30`.

### ⚠️ Critical Caveat: Interaction with `zoomType`

The `zoomLevel` feature does not apply when the `zoomType` is set to either `fullscreen` or `adaptive`. These two modes handle the vehicle's sizing automatically to guarantee optimal display:

* `fullscreen`: Automatically scales the vehicle to fill the entire canvas.
* `adaptive`: Dynamically resizes the vehicle to a maximized size while factoring in all available angles (essential for 360° consistency).

To use `zoomLevel`, you must ensure that `zoomType` is set to `relative`.

#### Override Example for 360° Views

By default, 360° views (`angle=200` to `231`) use `zoomType=adaptive`. If you need to manually control the magnification for a 360° sequence (which we generally advise against as it disrupts smoothness), you must override the default setting:

Code snippet

```html
// Manually controls magnification for an angle by forcing the 'relative' mode
...&zoomType=relative&angle=205&zoomLevel=15
```

### Best Practice Recommendation

We recommend using `zoomLevel` only when displaying a single, specific static angle (`angle=01` to `33`) where a desired magnification is required. Avoid using it for a full 360° spinner unless you fully understand the impact of overriding the default `adaptive` behavior.

### \&zoomLevel=0

<figure><img src="https://cdn-08.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=smart&#x26;modelFamily=fortwo&#x26;modelRange=fortwo&#x26;angle=05&#x26;zoomlevel=0" alt=""><figcaption></figcaption></figure>

### \&zoomLevel=30

<figure><img src="https://cdn-08.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=smart&#x26;modelFamily=fortwo&#x26;modelRange=fortwo&#x26;angle=05&#x26;zoomlevel=30" alt=""><figcaption></figcaption></figure>
