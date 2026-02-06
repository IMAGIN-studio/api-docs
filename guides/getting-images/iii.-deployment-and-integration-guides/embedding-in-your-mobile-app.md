# 📱 Embedding in Your Mobile App

## **Browser Referrer Headers in API Calls: A Guide for Mobile App Developers**

### Overview

Referrer headers in browser-based API calls are essential for tracking the origin of a request. They are particularly crucial in mobile applications for security, analytics, and personalization. This section provides an overview of how to set up referrer headers in API calls for mobile apps, with code samples in Swift, Java, and Flutter.

### Understanding Referrer Headers

A \`Referer\` header is a part of the HTTP request sent from a client to a server, typically a web browser to a web server. It contains the URL of the request's originating page. In mobile apps, it can be used to verify that the request is coming from a legitimate source, such as the app itself or a specific page within the app.

### Setting Up Referrer Headers in Mobile Apps

#### 1. Swift (iOS)

```
Unset
var urlComponents = URLComponents(string: "https://cdn.imagin.studio/getImage")
urlComponents?.queryItems = [
    URLQueryItem(name: "customer", value: "yourCustomerValue")
]
// Add more query items as needed

var request = URLRequest(url: (urlComponents?.url)!)
request.httpMethod = "GET"
request.setValue("https://myapp.com", forHTTPHeaderField: "Referer")

let task = URLSession.shared.dataTask(with: request) { (data, response, error) in
    // Handle response here
}
task.resume()
```

&#x20;  This sets the \`Referer\` header to "https://myapp.com" for the API call.

#### 2. Java (Android)

In Java for Android, use `HttpURLConnection` or a library like `OkHttp` to set custom headers:

```
Unset
URL url = new URL("https://cdn.imagin.studio/getImage?customer=yourCustomerValue");
// Add more query parameters as needed
HttpURLConnection connection = (HttpURLConnection) url.openConnection();
connection.setRequestMethod("GET");
connection.setRequestProperty("Referer", "https://myapp.com");

// Handle response
InputStream inputStream = connection.getInputStream();
// ...
```

&#x20;  This example sets the \`Referer\` header for the request.

#### 3. Flutter

&#x20;With Flutter, you can use the \`http\` package to make HTTP requests and set headers:

```
Unset
import 'package:http/http.dart' as http;

var url = Uri.parse('https://cdn.imagin.studio/getImage?customer=yourCustomerValue');
// Add additional query parameters here
var response = await http.get(url, headers: {'Referer': 'https://myapp.com'});
print('Response status: ${response.statusCode}');
```

&#x20;This sends a GET request with a custom \`Referer\` header.

## Best practices

* Share your data for faster results. We'll streamline your workflow, prioritize the right images, and improve the service we provide based on your needs.
* Be mindful of privacy concerns; avoid including sensitive or personally identifiable information in referrer URLs.
* For enhanced security, use referrer headers in conjunction with other authentication and authorization mechanisms.
* Ensure the referrer URL is consistent and correctly represents the source of your API calls.

## Conclusions

Setting up referrer headers in API calls from mobile apps is a straightforward process that can greatly aid in ensuring the integrity and traceability of requests. By following the code samples and best practices outlined above, developers can effectively implement this feature in their mobile applications.

## TTL in a Mobile app&#x20;

All our API requests have a Time to Live (TTL) of a maximum of 7 days. In a web browser, the TTL, which is found in the header, is always respected. However, in mobile apps, it is necessary to implement this functionality yourself. This because, in many cases, the app will make a new request every time a previous request is made. The application developer must adhere to the headers’ TTL (maximum of 7 days) and implement it for local caching of the image. By doing so, any updates made to the image will be adopted and compliance with the licensing agreement is assured.
