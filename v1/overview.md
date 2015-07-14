> **Notice**: API v1 is deprecated, has no official support, and will be no longer usable soon.

> Base URL: https://api.nerdbot.tv/1.0

### Anonymous API methods
    /commands
      ?user=[twitch name] 
Gets the command list.


    /songs
     ?user=[twitch name] 
Gets the current song and request list.

### Authenticated API methods
    /setcommand
      ?key=[api key]
      &name=[command name]
      &response=[command response]
      &resetuses=[set command uses to 0 if 'true']
      &allowfor=[all, subs, mods] 
Sets a command.


    /deletecommand
      ?key=[api key]
      &name=[command name] 
Deletes a command.


    /addsong
      ?key=[api key]
      &id=[song id]
      &from=[optional: 'added by' name] 
Adds a song request.
