# Responses

## Success

<aside class="notice">The WebriQ API uses the following success codes.</aside>

Success Code | Meaning
---------- | -------
200 | OK -- The request has succeeded.
201 | Created -- The request has been fulfilled and resulted in a new resource being created


## Errors

<aside class="notice">The WebriQ API uses the following error codes:</aside>

Error Code | Meaning
---------- | -------
400 | Bad Request -- Check whether your query is correct
401 | Unauthorized -- Your API is incorrect
403 | Forbidden -- The requested action can't be performed at your current authorization level
404 | Not Found -- The specified resource could not be found
405 | Method Not Allowed -- You tried to access a resource with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
429 | Too Many Requests -- You're requesting too much cowboy! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
