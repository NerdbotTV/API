# Users

These are people who have signed in on the Nerdbot dashboard.

|Endpoint|Description|
|---|---|
|[GET /users/:id](#get-usersid)|Gets a user's info|
|[PATCH /users/:id](#patch-usersid)|Updates a user's info|

## `GET /users/:id`
Gets a user's info. Some details will be hidden without a valid [access token](../authentication.md) with scope `view_user`.

#### Example Request
    GET https://api.nerdbot.tv/v3/users/2454512
#### Example Response
```JSON
{
    "id": 2454512,
    "sites": {
        "twitch": {
            "id": 37802347,
            "name": "rtainc"
        }
    },
    "mode": "on",
    "twitch_token": "J1qK1c18UUGJFAzz9xnH56584l4",
    "twitch_login": {
        "name": "RtaincsBot",
        "token": "FJ87fefJHH833fjeEFk9343JJF3"
    },
    "timers": {
        "sets": {
            "default": {
                "interval": "PT5M"
            },
            "promo": {
                "interval": "PT5M"
            }
        },
        "min_lines": 5
    },
    "song_requests": {
        "allow_from": ["moderators", "subscribers"],
        "volume": 50,
        "filter_mode": "strict",
        "max_requests_per_user": 3,
        "max_song_length": "PT5M"
    },
    "anti_spam": {
        "max_caps": 8,
        "max_emotes": 8,
        "notice_type": "chat",
        "allow_links_from": [],
        "ignore_subs": false
    },
    "plus": {
        "active": true,
        "profile": "EJ-JIe8fh3hfJFk",
        "started": "2017-01-01",
        "months_left": 0
    }
}
```
## `PATCH /users/:user`
Sets option(s) for a user. Requires a valid [access token](../authentication.md) with scope `edit_user`.

|Parameter|Optional|Type|Description|
---|---|---|---
```
#### Example Request
    PATCH https://api.nerdbot.tv/v3/users/2454512
            song_requests[volume]=25
            &timers[sets][default][interval]=PT60M
#### Example Response
```JSON
{
    "timers": {
        "sets": {
            "default": {
                "interval": "PT1H"
            }
        }
    },
    "song_requests": {
        "volume": 25
    }
    ...
}
```
