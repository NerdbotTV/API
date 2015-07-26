# NerdBot API
The NerdBot API is a feature-rich and constantly expanding way to manage a NerdBot instance remotely. The current and supported version is `v2`. All API calls must be over SSL (https).

Base URL: https://api.nerdbot.tv/v2/

## Pretty Print
By default, all responses use JSON Pretty Print for human readability. To make faster API calls in production, we recommend adding `?pretty=false` to all URLs.

## Response Format
All responses are formatted in JSON by default. All requests to `api.nerdbot.tv` have CORS support, and we have no immediate plan to implement JSONP support.

## Dates, Times, and Intervals
All dates, times, and intervals are in ISO 8601 format with UTC times. You can read the full standards [here](https://en.wikipedia.org/wiki/ISO_8601), but here's the TL;DR:

Human|ISO 8601
---|---
July 15, 2015 6AM|2015-07-15T06:00Z
2PM|14:00
60 minutes|PT1H *or* PT60M

## Error Format
Errors in `v2` are formatted as

    {
      "status": 401,
      "error": "Unauthorized",
      "message": "Missing or invalid access_token"
    }
