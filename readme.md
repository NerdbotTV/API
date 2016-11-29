# Nerdbot API
The Nerdbot API is a feature-rich and constantly expanding way to manage a Nerdbot instance remotely. The current and supported version is `v5`. It is a ground-up rewrite of the API with improved stability, security, and style. `v3` has been deprecated and will be removed soon.

Base URL: https://api.nerdbot.tv/5/

All API calls must be over SSL (https).

## Request Format
Any POST/PUT/PATCH parameters can be sent in JSON or form-encoding. For example, the following two bodies are identical:

    {"songs":{"volume":50}}

and

    songs[volume]=50

## Response Format
All responses are formatted in JSON. All requests to `api.nerdbot.tv` have CORS and JSONP support through the `?callback=` parameter.

## Dates, Times, and Intervals
All dates, times, and intervals are in ISO 8601 format with UTC times. You can read the full standards [here](https://en.wikipedia.org/wiki/ISO_8601), but here's the TL;DR:

Human (UTC)|ISO 8601
---|---
July 15, 2015 6AM|2015-07-15T06:00Z
2PM|14:00
60 minutes|PT1H *or* PT60M

## Error Format
Errors in `v5` are formatted as the following, with the HTTP status code stating the general error type (e.g. 404 Not Found).

    {
      "error": "Message about the error"
    }
