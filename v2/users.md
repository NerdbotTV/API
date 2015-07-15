# Users

These are someone who has connected with Twitch on the NerdBot dashboard.

|Endpoint|Description|
|---|---|
|[GET /users/:user](#get-usersuser)|Gets a user's bot options.|
|[PATCH /users/:user](#patch-usersuser)|Sets option(s) for a user.|

## `GET /users/:user`
Gets a user's bot options. Some options will be hidden without a valid [access token](../authentication.md) with scope `manage_bot`.

#### Example Request
    GET https://api.nerdbot.tv/v2/users/test_user
#### Example Response
    {
      "name": "test_user",
      "display_name": "Test_User",
      "enabled": true,
      "volume": 50,
      "timer_length": "PT5M"
    }
    
## `PATCH /users/:user`
Sets option(s) for a user. Requires a valid [access token](../authentication.md) with scope `manage_bot`.

|Parameter|Optional|Type|Description|
|---|---|---|---|
|volume|yes|int|Volume of song requests (0-100)|
|enabled|yes|bool|Whether or not the bot is enabled for the user|
|timer_length|yes|string|Length between timers in ISO-8601 interval format|

#### Example Request
    PATCH https://api.nerdbot.tv/v2/users/test_user
            volume=25
            &timer_length=PT1H
#### Example Response
    {
      "name": "test_user",
      "display_name": "Test_User",
      "enabled": true,
      "volume": 25,
      "timer_length": "PT1H"
    }
