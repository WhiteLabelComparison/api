# Errors

The White Label Comparison API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request was formatted incorrectly
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- Your API key does not provide access to this feature
404 | Not Found -- The endpoint you requested was not found
410 | Gone -- The item requested has been removed from our servers
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
