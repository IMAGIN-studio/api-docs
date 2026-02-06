# Getting Started

## Introduction to IMAGIN.studio Playbook Rules

{% hint style="info" %}
Let us handle the mapping. **Providing your data streamlines the process, ensuring seamless mapping, prioritized image selection, and an ever-evolving service.** Your data fuels the CDN!
{% endhint %}

### We offer access to an ever expanding CDN, serving you billions of unique images. We connect these images to many car specification data sets, including yours. The data agnostic imagery of every product that your customers want to see is the very heart of our service.

We provide the relevant imagery in the relevant place in a relevant format in time to support your marketing and sales campaigns, with as little of your effort as possible.

#### ALWAYS STRAIGHT FROM OUR CDN

The images are and remain property of IMAGIN.studio. We do not sell the images to you as a customer, but instead sell one Micro Use License for each requested image from the _getImage_ API.&#x20;

Unless otherwise stated in the agreement, our images may never be downloaded, cached on server side, distributed or modified by our customers. End user browser caching is accepted. Images may only be used straight from our CDN by using one of the available API's. This also ensures you have at all times the best version available of the images you are looking for.

#### USE THE CORRECT API AND DATA POINTS

IMAGIN.studio's CDN offers several APIs to fit the different implementation needs across the vast automotive ecosystem. It's important you use the appropriate one and use it as intended. These API's all operate on a subset of our generic attributes and corresponding source data. [read more](cdn-data-points.md)

#### INCLUDE PAINT SWATCHES / TILES ON YOUR PAGES

You may retrieve color information needed to create color tiles, which we call swatches, in your front-end code using the [paint API's](paint-data-and-api-behavior.md), which grants a Micro Use License to the end user for a single download/use of the returned data for the duration of the users' session.

#### IMAGIN.STUDIO SUITE

If you desire to browse through the image offering, grab an image URL and use it your CMS, like any other digital asset management solution does, then visit [https://dashboard.imagin.studio/](https://dashboard.imagin.studio/)

You will find features here to tailor and customize your images, request missing paints, verify how your data is matched to content, cars coming soon and more. read more

#### IMAGE CREATION UPON FIRST TIME REQUEST

You can potentially request any of the billions of unique images that our CDN has to offer. Producing each possible image ahead of time would be an impossible task, which is is why our CDN creates images when a specific image is requested for the first time and then stores it into cache for any further use. [read more](https://docs.imagin.studio/getImageAPI)

## Starting Your Implementation

You can fetch content through a URL fetch request at any of our APIs. A request is always formatted the same way:

https://{cdn-instance}.imagin.studio/{api-name}?customer={customer-key}&{query parameters}

#### CDN-INSTANCE

By default this CDN instance to use is 'cdn'. If however you wish to bypass the maximum server connections that Chrome allows simultaneously, then you may desire to any of the numbered cdn instances :: cdn-01 | cdn-02 | … | cdn-09

#### API-NAME

API's that we currently have in place for you ::

* /getImage [read more](getimage-api-behavior-and-timing.md)
* /getPaintSwatches [read more](paint-data-and-api-behavior.md#getpaintswatches)

#### CUSTOMER-KEY

Always apply your customer key to each API request. If you don't know your customer key, you can request this information at _service@imagin.studio ._

#### QUERY-PARAMETERS

The CDN attempts to match the data points you provide to the content it has to offer. The more data points you supply in your requests, the more accurate the returned content will be. Make sure to provide the mandatory data points and feel free to specify as many additional ones as you desire.\
Please only provide the relevant data. Please do not provide data like 'default' or 'unknown', but simply leave an attribute out of the request or leave the attribute empty if no relevant data is available.

Find the data points used by the IMAGIN.studio's CDN [here](https://docs.imagin.studio/cdnDatapoints).

**Share your data for faster results. We'll streamline your workflow, prioritize the right images, and improve the service we provide based on your needs**
