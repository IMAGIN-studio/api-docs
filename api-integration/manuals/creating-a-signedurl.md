# Creating a signedUrl

A signed URL is a secured version of a standard IMAGIN.studio CDN request. The request parameters are masked, making it much harder for unauthorised parties to copy your customer key and use it on their own website.

{% hint style="info" %}
Important Considerations\
\
While signed URLs enhance security, there are specific behaviors regarding caching and updates that your development team must be aware of to ensure your website always displays the most accurate imagery.
{% endhint %}

## Signed URL Lifecycle & Caching Behavior

A signed URL is a masked representation of your request parameters and your `customerKey`. The `/getSignedUrl` endpoint is fully deterministic: passing identical parameters will always output the exact same signed string. There is no timestamp, salt, or automated expiration built into the URL.

* URL Lifetime: A signed URL remains valid for as long as your customer account exists. Individual signed URLs cannot be revoked or invalidated once issued.
* Storage Recommendation: Because signed URLs are permanent and deterministic, there is no benefit to generating them dynamically on every user request. You can safely store and reuse generated signed URLs in your database or CMS.

## Secret Key Hygiene & Rotation

As a security best practice, we strongly encourage regularly rotating your `customerSecret` and retiring old ones.

* Periodic Rotation: Generating a new `customerSecret` on a regular cadence ensures that credentials used to access the `/getSignedUrl` API remain secure.
* Credential Scope: The `customerSecret` is passed exclusively in the HTTP `Authorization` header when authenticating to the `/getSignedUrl` endpoint and is not part of the generated string. Rotating or retiring an older secret prevents unauthorized parties from generating new signed URLs; all previously generated signed URLs will continue to function normally.

## How Library Updates and Corrections Propagate

The CDN does not evaluate cache hits based on the URL string. When an incoming request arrives—whether signed or bare—the CDN derives its cache key strictly from recognized rendering parameters (e.g., make, model, angle, paint, width, format, zoom, background). Unrecognized parameters are ignored and not included in the cache key.

* Image Corrections & Remappings: When an image correction or mapping adjustment is deployed on our end for an existing configuration, the signed URL does not change. You do not need to regenerate your signed URLs.
* Cache Resolution: The corrected image will appear automatically at your existing signed URL once the natural CDN cache TTL expires.

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
