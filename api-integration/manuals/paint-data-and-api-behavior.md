# Paint Data & API Behavior

{% hint style="info" %}
Let us handle the mapping. **Providing your paint data streamlines the process, ensuring seamless mapping, prioritized image selection, and an ever-evolving service.** Your data fuels the CDN!
{% endhint %}

### Do you have any API that returns the list of available color codes or description in a json format response?

Yes we do. Although few things need to be considered.

* A car paint from from most brands is often available in some countries and not in others.
* A car paint can be known by a host of different product codes.
* A car paint might be available on one vehicle but not on another, and even differ between markets.
* In rare occasions, one paint code may be used to classify two different paints by the same car brand.
* A car paint may be available but could be yet to be known on the CDN.
* This paint may exist in IMAGIN.studio's paint library, but never have been requested on the specific car you are looking for.

Related APIs:

#### GETPAINTSWATCHES

This API prodives a the colour information to create paint tiles / colour swatches with

#### GETPAINTS

This API provides a list of all paint combinations known in our library



## getPaintSwatches API

The IMAGIN Paint Swatch API provides an efficient way to obtain RGB color information of the primary, secondary and tertiary spray cans used for any given paint code.

#### API ENDPOINT

https://cdn.imagin.studio/getPaintSwatches?\&customer={customerId}make={make}\&paints={paints}

#### QUERY STRING DATA POINTS

make :: accepts the car make/brand as a concatenated string (e.g. tesla)\
paints :: accepts an array of OEM paint codes to retrieve (e.g. pbsb,pmng)\
customer :: a mandatory attribute for every API we offer

#### EXAMPLE

`https://cdn.imagin.studio/getPaintSwatches?customer={yourcustomerkey}&make=tesla&paints=pbsb,pmng,ppmr,ppsb,ppsw`

#### RETURNS JSON

primarySprayCan\
secondarySprayCan (if applicable)\
tertiarySprayCan (if applicable)

```
                {
                    "make": "tesla",
                    "paints": {
                        "pbsb": {
                            "paintId": "psp0319",
                            "paintDescription": "obsidian",
                            "primarySprayCan": {
                                "sprayCanId": "pbsb",
                                "paintType": "normal",
                                "primarySprayCanRGB": "#1e1e1e",
                                "primarySprayCanHighLightRGB": "#252525",
                                "colourCluster": "dark grey"
                            }
                        },
                        "pmng": {
                            "paintId": "psp00054",
                            "paintDescription": "midnight silver (metallic)",
                            "primarySprayCan": {
                                "sprayCanId": "pmng",
                                "paintType": "normal",
                                "primarySprayCanRGB": "#77787c",
                                "primarySprayCanHighLightRGB": "#929398",
                                "colourCluster": "grey"
                            }
                        }
                    }
                }
```

## getPaints API

The IMAGIN Paint Swatch API provides an efficient way to obtain paint availability, mapping and RGB color information of the primary, secondary and tertiary spray cans.

#### API ENDPOINT

For requesting available paints per make

`https://cdn.imagin.studio/getPaints?&customer={customerId}&target=make&make={make}`

For requesting available paints with specific car details

`https://cdn.imagin.studio/getPaints?&customer={customerId}&target=car&make={make}modelFamily={modelFamily}(&...other optional properties)[&paintIds=paint1,paint2]`

The (optional) properties include modelRange, modelVariant, bodySize, modelYear, trim, and powerTrain. A description of these properties can be found [here](cdn-data-points.md#data-points). With the optional property paintIds a filter can be applied to the result set. List up to 10 comma separated paintId's here to limit the result set.

#### RETURNS JSON

```
                {
                    "paintData": {
                        "target": "car",
                        "make": "audi",
                        "modelFamily": "a1",
                        "modelRange": "0",
                        "modelVariant": "0",
                        "bodySize": null,
                        "modelYear": "2022",
                        "trim": "eu",
                        "powerTrain": null,
                        "paintCombinations": {
                            "pspc0101": {
                                "mapped": {
                                    "2ypa": {
                                        "paintDescription": "glacier-white-metallic",
                                        "nativePaintDescriptions": [],
                                        "orderable": true,
                                        "available": true
                                    }
                                },
                                "paintSwatch": {
                                    "primary": {
                                        "highLight": "#abacb1",
                                        "lowLight": "#aeaead"
                                    }
                                }
                            }
                        }
                    }
                }
```

The result payload provides a list of paints (paintcombinations). Per paint the codes which are mapped to that particular paint combination is shown. If a paint is know to be available from the manufacturer it is listed as orderable = true. When the target=car property is used the result set will also include the available flag, indicating if rendering has already taken place, or rendering will take place on the first request.

