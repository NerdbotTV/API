# Songs
Songs are requested by users and played on-stream.

Endpoint|Description
---|---
[GET /users/:user/songs](#get-usersusersongs)|Gets the song queue of `:user`
[GET /users/:user/songs/:song](#get-usersusersongssong)|Gets a song (from its ID, `:song`) from the queue
[DELETE /users/:user/songs/:song](#delete-usersusersongssong)|Deletes a song (from its ID, `:song`) from the queue
[POST /users/:user/songs](#post-usersusersongs)|Adds a song to the queue

## `GET /users/:user/songs`
Gets the song queue of `:user`.
#### Example Request
    GET https://api.nerdbot.tv/v2/users/test_user/songs
#### Example Response
    [
      {
        "id": 2935,
        "title": "Major Lazer - Be Together (feat. Wild Belle) (Official Lyric Video)",
        "site": "youtube",
        "site_id": "S1g4Uoqhhc8",
        "url": "https://www.youtube.com/watch?v=S1g4Uoqhhc8",
        "length": "PT3M54S",
        "user": 1,
        "playing": false,
        "added_by": "Test_User_2"
      }
    ]
## `GET /users/:user/songs/:song`
Gets a song (from its ID, `:song`) from the queue.
#### Example Request
    GET https://api.nerdbot.tv/v2/users/test_user/songs/2935
#### Example Response
    {
      "id": 2935,
      "title": "Major Lazer - Be Together (feat. Wild Belle) (Official Lyric Video)",
      "site": "youtube",
      "site_id": "S1g4Uoqhhc8",
      "url": "https://www.youtube.com/watch?v=S1g4Uoqhhc8",
      "length": "PT3M54S",
      "user": 1,
      "playing": false,
      "added_by": "Test_User_2"
    }
    
## `DELETE /users/:user/songs/:song`
Deletes a song (from its ID, `:song`) from the queue.  Requires a valid [access token](../authentication.md) with scope `manage_songs`.
#### Example Request
    DELETE https://api.nerdbot.tv/v2/users/test_user/songs/2935
> You will receive an empty body and a 204 No Content response.
    
## `POST /users/:user/songs`
Resets stats for the `:viewer` of `:user`. Requires a valid [access token](../authentication.md) with scope `manage_songs`.

Parameter|Optional|Type|Description
---|---|---|---
song|no|string|An identifier for the song (e.g. Soundcloud URL or YouTube Search term)
from|yes|string|The name to show under `Added By`.

#### Example Request
    POST https://api.nerdbot.tv/v2/users/test_user/songs
           song=be together wild belle
           &from=Test_User
#### Example Response
```JSON
    {
      "id": 2936,
      "title": "Major Lazer - Be Together (feat. Wild Belle) (Official Lyric Video)",
      "added_by": "Test_User",
      ...
    }
```
