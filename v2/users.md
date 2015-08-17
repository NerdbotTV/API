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
  "use_points": true,
  "points_command": "!coins",
  "points_singular": "Coin",
  "points_plural": "Coins",
  "points_payout": 10,
  "points_payout_length": "PT5M",
  "points_for_song": 20,
  "use_song_filter": true,
  "max_requests": 3,
  "topic": "Welcome to the channel!",
  "topic_static": "Follow me on Twitter! https://twitter.com/RtaincCo",
  "topic_status": true,
  "list_commands": true
}
```
## `PATCH /users/:user`
Sets option(s) for a user. Requires a valid [access token](../authentication.md) with scope `manage_bot`.

|Parameter|Optional|Type|Description|
---|---|---|---
enabled|yes|bool|Enables the bot for the user
volume|yes|int|Volume of song requests (0-100)
timer_length|yes|string|Length between timers in ISO-8601 interval format
thank_followers|yes|bool|Enables "thank you" messages for new followers
timeout_notice_type|yes|string|Where to put timeout notices (`chat`, `whisper`, or `none`)
timeout_length|yes|string|The length of the timeout in ISO-8601 interval format.
sub_message|yes|string|Message sent upon new subscribers.
resub_message|yes|string|Message sent upon a subscriber's monthly anniversary
max_caps|yes|int|How many capital letters may be used in a row
max_emotes|yes|int|How many emotes may be used in a message
allow_links|yes|string|Who can post links (`all`, `subs`, or just `mods`)
use_points|yes|bool|Enabled the payouts of points to viewers
points_command|yes|string|The command used for the points system
points_singular|yes|string|Singular name of the points
points_plural|yes|string|Plural name of the points
points_payout|yes|int|How many points is paid out
points_payout_length|yes|string|Time between payouts
points_for_song|yes|int|XP count required for a song request. 0 to disable
use_song_filter|yes|bool|Enables the global song filter (**changing soon!**)
max_requests|yes|int|Max amount of song requests per requester
topic|yes|string|The channel's topic
topic_static|yes|string|Appended to the channel's topic
topic_status|yes|bool|Enables the stream title in the channel's topic
list_commands|yes|bool|Enables the command list at `nerdbot.tv/commands/test_user`

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
