# Errors


The ARDX Open API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Invalid request
401 | Unauthorized -- Your API key is incorrect
403 | Forbidden -- The supplied API key is not authorized for this request
404 | Not Found -- The specified result set could not be found
405 | Method Not Allowed -- Attempt to access with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
410 | Gone -- The reult set requested has been removed from our servers
429 | Too Many Requests -- Exceeded request limit
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
