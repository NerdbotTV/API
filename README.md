## Overview
The NerdBot API is a feature-rich and constantly expanding way to manage a NerdBot instance remotely. The current version is `v2` -- `v1` is now deprecated and will not be functional much longer. All API calls must be over SSL (https).

Base URL: https://api.nerdbot.tv/v2/

## Response Format
All responses are formatted in JSON by default. All requests to `api.nerdbot.tv` have CORS support, and we have no immediate plan to implement JSONP support.

## Error Format
Errors in `v2` are formatted as

    {
      "status": 401,
      "error": "Unauthorized",
      "message": "Missing or invalid access_token"
    }
