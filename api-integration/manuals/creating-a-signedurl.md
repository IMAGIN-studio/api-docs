# Creating a signedUrl

## 1. Obtain API Credentials:

Obtain your CDN API credentials, which consist of a "customerId" (username) and a "customerSecret" (password) specific to your CDN account. The customerId is what is used to connect to the CDN for front-end calls. The customerId and customerSecret can be found in the[ dashboard](https://docs.imagin.studio/faq/dashboard).

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
