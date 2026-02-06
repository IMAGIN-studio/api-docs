# CORS headers

For our images as well as our JSON APIs we set the following CORS headers:

```
Access-Control-Allow-Headers: *
Access-Control-Allow-Methods: GET, HEAD, OPTIONS
Access-Control-Allow-Origin: *
Access-Control-Expose-Headers: *
```

This means that any calling website has cross origin access to our output to show images and read into JavaScript code.
