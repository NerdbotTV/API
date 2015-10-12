# Users

These are people who have connected with Twitch on the Nerdbot dashboard.

|Endpoint|Description|
|---|---|
|[GET /users/:user](#get-usersuser)|Gets a user's bot options|
|[PATCH /users/:user](#patch-usersuser)|Sets option(s) for a user|

## `GET /users/:user`
Gets a user's bot options. Some details will be hidden without a valid [access token](../authentication.md) with scope `info`.

#### Example Request
    GET https://api.nerdbot.tv/v3/users/test_user
#### Example Response
```JSON
{
    "id": 1,
    "name": "Test_User",
    "join": true,
    "timerInterval": "PT5M",
    "songs": {
        "enabled": true,
        "volume": 50,
        "filter": "strict",
        "maxRequests": 3
    },
    "points": {
        "enabled": true,
        "command": "!cash",
        "nameSingular": "dollar",
        "namePlural": "dollars",
        "payoutAmount": 10,
        "payoutInterval": "PT5M",
        "songCost": 15
    },
    "topic": {
        "text": "Welcome to the stream!",
        "title": false,
        "staticText": "Follow me on Twitter @RtaincCo"
    },
    "moderation": {
        "maxCaps": 8,
        "maxEmotes": 8,
        "noticeType": "whisper",
        "allowLinks": "mods",
        "subsCanSpam": false
    },
    "notices": {
        "subscriber": "Thanks {name} for subbing!",
        "resubscriber": "Thanks {name} for subbing {months} months in a row!",
        "follower": "/me Thank you {names} for following; you're number {twitch followercount}!"
    }
}
```
## `PATCH /users/:user`
Sets option(s) for a user. Requires a valid [access token](../authentication.md) with scope `manage`.

|Parameter|Optional|Type|Description|
---|---|---|---
join|yes|bool|Enables the bot for the user
timerInterval|yes|string|Amount of time between timers
songs[enabled]|yes|bool|Enables the song request commands
songs[volume]|yes|int|Volume of song requests (0-100)
songs[filter]|yes|string|Song filter type (`off`, `normal`, `strict`)
songs[maxRequests]|yes|int|Max amount of song requests per requester
points[enabled]|yes|bool|Enables point commands and payouts
points[command]|yes|string|The command for points
points[nameSingular]|yes|string|The singular name for points
points[namePlural]|yes|string|The plural name for points
points[payoutAmount]|yes|int|Amount of points to payout
points[payoutInterval]|yes|string|Time between point payouts
points[songCost]|yes|int|Amount of points required for a song request
topic[text]|yes|string|The channel's topic
topic[title]|yes|bool|Add the stream title to the topic
topic[static]|yes|string|Appended to the topic
moderation[maxCaps]|yes|int|Max caps in a row
moderation[maxEmotes]|yes|int|Max emotes in a message
moderation[noticeType]|yes|string|How to announce a timeout (`off`, `chat`, `whisper`)
moderation[allowLinks]|yes|string|Who can post links (`all`, `subs`, `mods`)
moderation[subsCanSpam]|yes|bool|Subs can ignore moderation settings
notices[subscriber]|yes|string|Message to send upon a new subscriber
notices[resubscriber]|yes|string|Message to send upon a resubscription
notices[follower]|yes|string|Message to send upon a new follower
```
#### Example Request
    PATCH https://api.nerdbot.tv/v3/users/test_user
            songs[volume]=25
            &timer_length=PT1H
#### Example Response
```JSON
{
  "timerInterval": "PT1H",
  "songs": {
    "volume": 25
  }
  ...
}
```
