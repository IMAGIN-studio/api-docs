# Creating a signedUrl

A signed URL is a secured version of a standard IMAGIN.studio CDN request. The request parameters are masked, making it much harder for unauthorised parties to copy your customer key and use it on their own website.

{% hint style="info" %}
Important Considerations\
\
While signed URLs enhance security, there are specific behaviors regarding caching and updates that your development team must be aware of to ensure your website always displays the most accurate imagery.
{% endhint %}

#### Dynamic vs. Static Generation

To ensure your website always serves the latest vehicle imagery, signed URLs must be dynamically generated on your end at the point of the request.

If signed URLs are static, any updates made within our library - such as a new vehicle release, a mapping change, or an image correction - will not be reflected on your website until the signed URL is regenerated.

* **Best Practice:** Generate signed URLs dynamically. This ensures that the correct images reflect eventually without any manual action required on your end.
* **Static Risk:** If your implementation relies on static signed URLs, you will need to manually regenerate them whenever a data update is released to pick up the latest changes.

#### Cache Flushing Limitations

Because signed URLs mask the request parameters, IMAGIN.studio is unable to manually flush the cache for these specific requests on your behalf.

In practice, this means that if a mapping update or an image correction is deployed on our end, the changes cannot be "forced" to appear via a manual flush of the signed URL. By following the dynamic generation strategy mentioned above, you bypass this limitation and allow the CDN to serve the updated content naturally as the dynamic URL parameters evolve.

***

## Implementation Guide

Follow these four steps to generate and deploy your signed URLs.

## 1. Obtain API Credentials:

Obtain your CDN API credentials, which consist of a "customerId" (username) and a "customerSecret" (password) specific to your CDN account. The customerId is what is used to connect to the CDN for front-end calls. The customerId and customerSecret can be found in the [dashboard](https://docs.imagin.studio/faq/dashboard).

## 2. Formulate API Request:

Prepare the request you want to send to the CDN API getSignedUrl, including any required parameters, headers, and payload according to the API's documentation.&#x20;

For instance: https://cdn.imagin.studio/getSignedUrl?make=audi\&modelFamily=a4

## 3. Include Authorization Header:

Add the \`Authorization\` header to your request. The value of this header should be the word "Basic" followed by a space and the Base64-encoded string of your "customerId:customerSecret" combination.

For example, if your "customerId" is "abc123" and your "customerSecret" is "xyz987", you need to Base64 encode the string "abc123:xyz987". This would result in the encoded value "YWJjMTIzOnh5ejk4Nw==". Add this to the \`Authorization\` header in the format: \`Authorization: Basic YWJjMTIzOnh5ejk4Nw==\`.

## 4. Add the created code to your URL Request:

Send the prepared HTTP request to the CDN API server, by just attaching the returned string to https://cdn.imagin.studio/{signedURL}

That's it! Following these steps, you can connect to the CDN API by including the "customerId" as the username and the "customerSecret" as the password in the \`Authorization\` header.

<br>
