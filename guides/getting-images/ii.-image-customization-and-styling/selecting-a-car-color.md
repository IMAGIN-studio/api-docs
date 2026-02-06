# 🎨 Selecting a Car Color

{% hint style="info" %}
Let us handle the mapping. **Providing your data streamlines the process, ensuring seamless mapping, prioritized image selection, and an ever-evolving service.** Your data fuels the CDN
{% endhint %}

***

## Selecting a Car Color: Dynamic Paint Customization

Our API enables highly accurate and realistic paint visualization. To ensure the highest degree of color accuracy and reliability, we recommend using both the `paintId` and `paintDescription` parameters in your `getImage` request.

### Achieving Maximum Color Accuracy

The appearance of paint is highly dependent on light and environment. Our team uses dedicated methods to map color data to achieve the most realistic representation possible.

<table data-header-hidden><thead><tr><th width="148.19140625"></th><th width="346.15625"></th><th width="110.8984375"></th><th></th></tr></thead><tbody><tr><td><strong>Parameter</strong></td><td><strong>Purpose</strong></td><td><strong>Required</strong></td><td><strong>Example Value</strong></td></tr><tr><td><mark style="background-color:yellow;">paintId</mark></td><td>The manufacturer's specific code for the paint color. This code is often sourced directly from a data provider of your choice (e.g., CAP HPI).</td><td>Required</td><td><code>6w9</code></td></tr><tr><td><mark style="background-color:purple;">paintDescription</mark></td><td>The human-readable name associated with the paint color. This can be the OEM color name or an equivalent identifier.</td><td>Required</td><td><code>radiant-green</code></td></tr></tbody></table>

Best Practice: Always use both `paintId` and `paintDescription` together. The description provides essential fallback information that aids our research if the `paintId` cannot be immediately resolved, ensuring continuous improvement in paint accuracy.

### Request Example: Specifying Color

To request a specific color, append the parameters to your base vehicle request:

https://cdn.imagin.studio/getImage?customer={customer-key}\&make=toyota\&modelFamily=yaris\&modelVariant=ha\&zoomtype=fullscreen<mark style="background-color:yellow;">\&paintId=6w9</mark><mark style="background-color:purple;">\&paintDescription=radiant-green</mark>

### Data Mapping and Flexibility

Our system streamlines the process of translating your internal color data:

* Intelligent Mapping: Providing your paint data streamlines our mapping process, ensuring seamless translation to the corresponding unique color identifiers on our CDN.
* Self-Learning Accuracy: Our algorithms continuously learn from new data, ensuring that paint representations become progressively more accurate and comprehensive over time.
* Unsupported Paints: If a provided `paintId` is not yet available on the CDN, the system uses the `paintDescription` to aid our research, allowing us to proactively add the requested color to our library.

| **Example Paint IDs and Descriptions** |
| -------------------------------------- |
| `6w9` - Radiant Green                  |
| `KHK` - Metallic Clay Orange           |
| `3U5` - Emotional Red metallic         |

{% hint style="info" %}
In order to ensure the highest degree of accuracy, "_paintIDs_" and "_paintDescriptions_" should always be used together.&#x20;
{% endhint %}

<div><figure><img src="https://cdn.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=toyota&#x26;modelFamily=yaris&#x26;&#x26;modelRange=yaris&#x26;modelVariant=ha&#x26;zoomtype=fullscreen&#x26;paintId=6w9&#x26;paintdescription=radiant-green" alt=""><figcaption><p>6w9 - Radiant Green</p></figcaption></figure> <figure><img src="https://cdn.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=toyota&#x26;modelFamily=yaris&#x26;&#x26;modelRange=yaris&#x26;modelVariant=ha&#x26;zoomtype=fullscreen&#x26;paintId=khk&#x26;paintdescription=metallic-clay-orange" alt=""><figcaption><p>KHK - Metallic Clay Orange</p></figcaption></figure> <figure><img src="https://cdn.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=toyota&#x26;modelFamily=yaris&#x26;&#x26;modelRange=yaris&#x26;modelVariant=ha&#x26;zoomtype=fullscreen&#x26;paintId=8u7&#x26;paintdescription=blue-electra" alt=""><figcaption><p>8U7 - Blue Electra</p></figcaption></figure></div>

<div><figure><img src="https://cdn.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=toyota&#x26;modelFamily=yaris&#x26;&#x26;modelRange=yaris&#x26;modelVariant=ha&#x26;zoomtype=fullscreen&#x26;paintId=D06&#x26;paintdescription=lightning-yellow" alt=""><figcaption><p>D06 - lightning yellow </p></figcaption></figure> <figure><img src="https://cdn.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=toyota&#x26;modelFamily=yaris&#x26;&#x26;modelRange=yaris&#x26;modelVariant=ha&#x26;zoomtype=fullscreen&#x26;paintId=175265&#x26;paintdescription=metallic-cardamom-green" alt=""><figcaption><p>3i - Python Green </p></figcaption></figure> <figure><img src="https://cdn.imagin.studio/getImage?&#x26;customer=img-test&#x26;make=toyota&#x26;modelFamily=yaris&#x26;&#x26;modelRange=yaris&#x26;modelVariant=ha&#x26;zoomtype=fullscreen&#x26;paintId=3U5&#x26;paintdescription=Emotional-Red-metallic" alt=""><figcaption><p>3U5 - Emotional Red metallic</p></figcaption></figure></div>

