# 🖥️ Embedding in Your Website

Let's make your car images a reality! Tell us the make, model, color, angle, and any other details you envision, so we can create the perfect visuals for you.

{% hint style="info" %}
Let us handle the mapping. **Providing your data streamlines the process, ensuring seamless mapping, prioritized image selection, and an ever-evolving service.** Your data fuels the CDN!
{% endhint %}

The quality of the image can be changed with the width command:

<table data-header-hidden><thead><tr><th width="95.33333333333331"></th><th width="520"></th><th></th></tr></thead><tbody><tr><td>width</td><td><p></p><p>The resolution of the image you wish to receive. Any requested width is resolved back to the first larger standard CDN size. For example 745 returns 800. All sizes are web optimized except for 3456, which offers with highest quality possible disregarding file size.<br></p></td><td><p></p><ul><li>150</li><li>400</li><li>800</li><li>1200</li><li>1600</li><li>2600</li><li>3456</li></ul></td></tr></tbody></table>

### the URL

The URL consists of four sections:

| <mark style="color:red;">END POINT</mark>         | IMAGIN.studio's CDN                |
| ------------------------------------------------- | ---------------------------------- |
| <mark style="color:green;">IDENTIFICATION</mark>  | Your customer key                  |
| <mark style="color:yellow;">CAR</mark>            | The vehicle you are looking for    |
| <mark style="color:blue;">CUSTOMISATION</mark>    | Specifications to adjust the image |

<mark style="color:red;">https://cdn.imagin.studio/getImage?</mark><mark style="color:green;">customer={customer-key}</mark><mark style="color:yellow;">&{car parameters}</mark><mark style="color:blue;">&{customization parameters}</mark>

## Example URL:

<mark style="color:red;">https://cdn.imagin.studio/getImage?</mark><mark style="color:green;">\&customer=xxx</mark><mark style="color:yellow;">\&make=bmw\&modelFamily=x6\&modelRange=x6\&modelVariant=od\&modelYear=2024\&powerTrain=hybrid\&transmission=0\&bodySize=5\&trim=eu\&paintId=pspc0007</mark><mark style="color:blue;">\&angle=23\&zoomtype=fullscreen\&position=bottom</mark><br>
