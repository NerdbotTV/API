# Viewers
Viewers are people that have entered a [User](users.md)'s chat. Some chatters may not have a viewer object immediately. Please respect that viewer objects and its API calls are very resource-intensive, hence why they are not provided by most other bots.

Endpoint|Description
---|---
[GET /users/:user/viewers/:viewer](#get-usersuserviewersviewer)|Gets the `:viewer` of `:user`
[PATCH /users/:user/viewers/:viewer](#patch-usersuserviewersviewer)|Updates stats for the `:viewer` of `:user`
[DELETE /users/:user/viewers/:viewer](#delete-usersuserviewersviewer)|Resets stats for the `:viewer` of `:user`

## `GET /users/:user/viewers/:viewer`
Gets the `:viewer` of `:user`. Requires a valid [access token](../authentication.md) with scope `points`.
#### Example Request
    GET https://api.nerdbot.tv/v3/users/test_user/viewers/test_viewer
#### Example Response
    {
      "name": "Test_Viewer",
      "points": 1000,
      "timeWatched": "PT5H20M"
    }
## `PATCH /users/:user/viewers/:viewer`
Updates stats for the `:viewer` of `:user`. Requires a valid [access token](../authentication.md) with scope `points`.

|Parameter|Optional|Type|Description|
|---|---|---|---|
|points|yes|int|The total points of `:viewer`|
|timeWatched|yes|string|The time `:viewer` has watched `:user`'s stream|

#### Example Request
    PATCH https://api.nerdbot.tv/v3/users/test_user/viewers/test_viewer
            time_watched=PT19500S
#### Example Response
    {
      "name": "Test_Viewer",
      "points": 1000,
      "timeWatched": "PT5H25M"
    }
