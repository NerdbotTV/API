# Users

These are someone who has connected with Twitch on the NerdBot dashboard.

|Endpoint|Description|
|---|---|
|[GET /users/:user](#get-usersuser)|Gets a user's bot options|
|[PATCH /users/:user](#patch-usersuser)|Sets option(s) for a user|

## `GET /users/:user`
Gets a user's bot options. Some details will be hidden without a valid [access token](../authentication.md) with scope `user_details`.

#### Example Request
    GET https://api.nerdbot.tv/v2/users/test_user
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
---|---|---|---
volume|yes|int|Volume of song requests (0-100)
enabled|yes|bool|Whether or not the bot is enabled for the user
timer_length|yes|string|Length between timers in ISO-8601 interval format
thank_followers|yes|bool|Whether or not new followers should be thanked in chat
timeout_notice_type|yes|string|Where to put timeout notices (`chat`, `whisper`, or `none`.)
timeout_length|yes|string|The length of the timeout in ISO-8601 interval format.
sub_message|yes|string|Message sent upon new subscribers.
resub_message|yes|string|Message sent upon a subscriber's monthly anniversary
max_caps|yes|int|How many capital letters may be used in a row
max_emotes|yes|int|How many emotes may be used in a message
allow_links|yes|string|Who can post links (`all`, `subs`, or just `mods`.)
xp_enabled|yes|bool|Whether or not users gain XP.
xp_payout|yes|int|How much XP is paid out.
xp_payout_length|yes|string|Interval between payouts.
xp_for_song|yes|int|XP count required for a song request. 0 to disable.

#### Example Request
    PATCH https://api.nerdbot.tv/v2/users/test_user
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
