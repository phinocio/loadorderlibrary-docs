# Errors

The Load Order Library API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- You can't access this resource.
404 | Not Found -- The specified resource could not be found.
405 | Method Not Allowed -- You sent a request to a resource with an invalid method.
429 | Too Many Requests -- You're requesting too many requests.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
