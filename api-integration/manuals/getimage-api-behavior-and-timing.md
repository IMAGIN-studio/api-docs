# getImage API Behavior & Timing

**Diving into the image production process will enhance your understanding of the CDN behavior and timing, allowing you to optimize your usage.**

{% hint style="info" %}
Let us handle the mapping. **Providing your data streamlines the process, ensuring seamless mapping, prioritized image selection, and an ever-evolving service.** Your data fuels the CDN!
{% endhint %}

You fetch any image by calling our _getImage_ image API using a URL with Query String parameters to tell us which image you wish to receive.

In order for the IMAGIN.studio CDN to deliver the desired image our CDN needs to:

* analyze your data;
* look for the vehicle you are asking for;
* look for the spray cans to create your paint;
* produce your car with your paint;
* adjust the image to your tailoring settings.

#### DATA TRAINING

The quality of our image matching relies 100% on the correct mapping of incoming customer data to internal IMAGIN images (from our perspective). So in order to get started, training the platform to understand your data is the first step.

The platform is learning about your data starting the moment you request your first image. You will notice that whenever you request images and receive placeholder images, new images will automatically appear soon after.

{% hint style="info" %}
_Tip when getting started :_ **Our data-driven system learns and adapts over time**. As it gathers information about your data structure, the implementation of your user experience will become increasingly streamlined and efficient. _However, if you have an initial car data export for us (CSV file), we can speed up the initial training._
{% endhint %}

#### CAR MODELS CREATION

Whenever we receive a request for a car model that we have not produced yet, we automatically start the production process. When the production is done images can be created.

#### PAINT DEFINITION

Aside from understanding your car data, the CDN must have the definition of the paint you are requesting on your car on file. Any new paint that is requested automatically triggers new paint creation in our Paint Studio. Once the paint is created, it can be used on any car.

#### IMAGE CREATION

When the IMAGIN.studio's CDN receives an image request from you, the requested car image is created for you automatically by our factory.

#### IMAGE TAILORING

If the requested image is created it is adjusted to meet your requested tailoring specifications. Tailoring settings include specific _width_, _fileType_, _offset_, _zoomType_, _zoomLevel_, licenseplate logo, among many others.

#### IMAGE DELIVERY VS IMAGE CREATION

The CDN can create billions of different specific images. Having all of the ingredients to make an image does not per se triggers image creation, as the volume would exceed a quadrillion images. Instead, you or your customers trigger an image creation when that picture has never been created before, which is then stored in the global CDN cache which includes all our customers. Hence, we only create the images that our customers are actually requesting.

**We consistently deliver high-performance image serving, handling hundreds of millions of requests monthly and effortlessly scaling to meet the demands of global campaigns.**

#### TIMING OF THE GETIMAGE API

In the event the image is not yet in cache, it will be created and put into the global CDN cache. The platform handles many different scenarios, yet the following are good to consider:

Three different substitute image can be shown.

<table><thead><tr><th width="184">Situation</th><th width="293.3333333333333">Result</th><th>Timing</th></tr></thead><tbody><tr><td>Car data is not understood by CDN yet</td><td>CDN triggers a data training assignment. Training starts immediately. Returned image: substitute image if partial data set is known, a speedShape if make and model are unknown</td><td>ETA returned image : 20ms to 300ms ETA data training: 1 to 3 business days to train the data</td></tr><tr><td>Car model has not yet been produced by IMAGIN.studio</td><td>CDN triggers model production for this missing car Returned image: speedShape Returned header: X</td><td>ETA speedShape image: 20ms to 300ms ETA missing model: 7 to 30 days to build the car</td></tr><tr><td>Car model exists, but with different trim details</td><td>CDN triggers trim production for this missing trim Returned image: requested car model but with alternative rim or bumper</td><td>ETA substitute image: 20ms to 300ms ETA new image: Unfortunately no expectation can be given, depends on overal production load of new model releases and new model year facelifts.</td></tr><tr><td>Paint requested has not been produced by IMAGIN.studio yet</td><td>CDN triggers paint definition assignment. Paint creation starts immediately. Image creation starts immediately after paint creation completed. Returned image: requested vehicle in light grey metallic Returned header: X-ImaginStudio-Performed-Matches includes paintId as a substituted value</td><td>ETA substitute image: 20ms to 1000ms ETA new image: 1 to 48 hours Refresh afterwards shows created image</td></tr><tr><td>Car has been created, the paint is known by the CDN, but the paint was never requested on the requested car before by anyone on the platform</td><td>CDN triggers image creation automatically. Production starts immediately Returned image: requested vehicle in light grey metallic Returned header: X-ImaginStudio-Performed-Matches includes paintId as a substituted value</td><td>ETA substitute image: 20ms to 1000ms ETA new image: 1 to 48 hours Refresh afterwards shows created image</td></tr><tr><td>Image has been created before, but not with your requested specific image resolution/offset/width/filetype/licenseplate</td><td>CDN triggers image tailoring automatically. Customization starts immediately. V2: Returned image: waitShape V3: Direct image response</td><td>V2: ETA 20 to 40 seconds, Refresh afterwards shows created image V3: ETA less then 3 seconds. In exceptional cases V3 may return a waitShape after 5 seconds. In this particular case the actual demand is too high and the creation is queued.</td></tr><tr><td>Requested image has been created before</td><td>Image is returned straight from CDN cache (no waitShape)</td><td>20ms and 300ms load time depending on file size and local internet connections</td></tr><tr><td>After 7 days the cache status of an image will be reconsidered.</td><td>A check is performed to validate if the images returend the last time is still the best choice. For example a new trim may have been introduced. (no waitShape)</td><td>1 to 2 second load time</td></tr></tbody></table>
