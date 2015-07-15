# Viewers
Viewers are people that have entered a [User](users.md)'s chat. Some chatters may not have a viewer object immediately. Please respect that viewer objects and its API calls are very resource-intensive, hence why they are not provided by most other bots.

|Endpoint|Description|
|---|---|
|[GET /users/:user/viewers/:viewer](#get-usersuserviewersviewer)|Gets the `:viewer` of `:user`.|
|[PATCH /users/:user/viewers/:viewer](#patch-usersuserviewersviewer)|Updates data for the `:viewer` of `:user`.|

## `GET /users/:user/viewers/:viewer`
Gets the `:viewer` of `:user`. Requires a valid [access token](../authentication.md) with scope `manage_xp`.
#### Example Request
    GET https://api.nerdbot.tv/v2/users/test_user/viewers/test_viewer
#### Example Response
    {
      "name": "test_viewer",
      "display_name": "Test_Viewer",
      "xp": 1000,
      "time_watched": "PT5H20M"
    }
## `PATCH /users/:user/viewers/:viewer`
Updates data for the `:viewer` of `:user`. Requires a valid [access token](../authentication.md) with scope `manage_xp`.

|Parameter|Optional|Type|Description|
|---|---|---|---|
|xp|yes|int|The total XP points of the viewer|
|time_watched|yes|bool|The time the viewer has watched user's channel|

#### Example Request
    PATCH https://api.nerdbot.tv/v2/users/test_user/viewers/test_viewer
            time_watched=PT5H25M
#### Example Response
    {
      "name": "test_viewer",
      "display_name": "Test_Viewer",
      "xp": 1000,
      "time_watched": "PT5H25M"
    }
