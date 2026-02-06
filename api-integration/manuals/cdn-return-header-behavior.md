# CDN Return Header Behavior



### CDN Return Header Behaviour&#x20;

This document explains how to interpret the response headers returned by our CDN when requesting an image. Understanding these headers can help you troubleshoot issues related to unexpected image delivery.

#### Header Attributes and Logic  The following header attributes provide information about the CDN's processing of your image request.<br>

1\. _x-imaginstudio-request-found_:

* Possible Values: True or False



* Meaning:

True: A matching image was found in the CDN cache or successfully generated. The image displayed is the one requested.

False: No matching image was found in the CDN cache, and the system was unable to generate the requested image. This might indicate an issue with the image request parameters or the source image.

<br>

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXePj9OCgPc_MqPox5EPGH0U2K9Il0PV0PiuGUVP_zsvCuaKvC5_mr1rNNSlINfWzMYr0azJnmybuOPjgO4-A-x4i9HfcwNVZJwbG8gTBlrPLfrFRgz2mROEjhajaXkTTV--_Al-?key=ob7Xody-qnRDnNuIZPCJiELP" alt=""><figcaption></figcaption></figure>

\
\
2\. _x-imaginstudio-request-resolved_:

* Possible Values: True or False



* Meaning:

True: The CDN successfully matched the request with a vehicle. This is relevant for speedshapes, where the system needs to identify the correct vehicle model to generate the image.

False: The CDN was unable to match the request with a vehicle. This could happen if the vehicle information in the request is incorrect or missing.

<br>

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfky6fj0fwqx2ZZDs3gOSqPtDBv5p7oPDqAVSjGkLVPjoUN_uxT6Th_a2UXDikfCEDf35jzomQNvVwZWfmzYcWqLTPXt4PEdFXDMOwzWf2BzpN3xtnO_TxO4bOWBSBIAofNJtT4fw?key=ob7Xody-qnRDnNuIZPCJiELP" alt=""><figcaption></figcaption></figure>

<br>

**Troubleshooting:**

By analyzing these headers, you can understand how the CDN processed your request and why a particular image was delivered. If the image is not as expected, you can use the information in the headers to identify the cause and adjust your request parameters accordingly.



ACCESS HEADERS WITH CODE

And of course you can also use scripting to read this information. You can find a sample of such code below.

```
  async function getImageHeaders(url) {
                        // input :: any IMAGIN.studio car image url (as string)
                        // let responseHeader = await getImageHeaders('https://cdn.imagin.studio/getImage?&make=audi&modelFamily=a4&angle=01');
                        // returns :: IMAGIN.studio near match information (as json object)
                    
                        // USEFUL HEADER ATTRIBUTES
                        // x-imaginstudio-request-found > boolean; if true the request was entirely satisfied
                        // x-imaginstudio-request-resolved > boolean; if true the request was succesfully near matched
                        // x-imaginstudio-performed-matches > json object; parameters and values that were substituted while near matching
                        return new Promise(async (resolve, reject) => {
                            try {
                                let request = new XMLHttpRequest();
                                request.open("HEAD", url);
                                request.onload = function () {
                                    const headers = {};
                                    request.getAllResponseHeaders()
                                        .trim()
                                        .split(/[\r\n]+/)
                                        .map(value => value.split(/: /))
                                        .forEach(keyValue => {
                                            if (keyValue[0] !== '') headers[keyValue[0]] = keyValue[1];
                                        });
                                    resolve(headers)
                                }
                                request.onerror = function () { resolve({}) };
                                request.responseType = "json";
                                request.send();
                            } catch (e) {
                                console.error(e);
                                resolve({});
                            }
                        });
                    }
                    
                    const imgUrl = 'https://cdn.imagin.studio/getImage?customer=yourKey&make=volkswagen&modelFamily=polo&paintId=imagin-white&angle=01';
                    async function readResponseHeader(imgUrl) {
                        let headers = await getImageHeaders(imgUrl);
                        console.log(headers.hasOwnProperty('x-imaginstudio-performed-matches') ? JSON.stringify(headers['x-imaginstudio-performed-matches'], null, 2) : 'request was satisfied');
                    }
```

