# Users

These are someone who has connected with Twitch on the NerdBot dashboard.

|Endpoint|Description|
|---|---|
|[GET /users/:user](#get-usersuser)|Gets a user's bot options|
|[PATCH /users/:user](#patch-usersuser)|Sets option(s) for a user|

## `GET /users/:user`
Gets a user's bot options. Some details will be hidden without a valid [access token](../authentication.md) with scope `user_details`.

#### Example Request
    GET https://api.nerdbot.tv/v2/users/1
#### Example Response
```JSON
{
  "id": 1,
  "name": "test_user",
  "display_name": "Test_User",
  "enabled": true,
  "volume": 50,
  "timer_length": "PT5M",
  "thank_followers": true,
  "timeout_notice_type": "chat",
  "timeout_length": "PT30S",
  "sub_message": "Thank you for subscribing, {sub}!",
  "resub_message": "Thanks {sub} for {months} months of subscribing!",
  "max_caps": 0,
  "max_emotes": 0,
  "allow_links": "subs",
  "xp_enabled": true,
  "xp_payout": 10,
  "xp_payout_length": "PT5M",
  "xp_for_song": 20
}
```
## `PATCH /users/:user`
Sets option(s) for a user. Requires a valid [access token](../authentication.md) with scope `manage_bot`.

|Parameter|Optional|Type|Description|
|---|---|---|---|
|volume|yes|int|Volume of song requests (0-100)|
|enabled|yes|bool|Whether or not the bot is enabled for the user|
|timer_length|yes|string|Length between timers in ISO-8601 interval format|

#### Example Request
    PATCH https://api.nerdbot.tv/v2/users/1
            volume=25
            &timer_length=PT1H
#### Example Response
```JSON
{
  "volume": 25,
  "timer_length": "PT1H"
  ...
}
```
