# Commands
Commands are an object owned by a [User](users.md).

Endpoint|Description
---|---
[GET /users/:user/commands](#get-usersusercommands)|Gets all commands for `:user`
[GET /users/:user/commands/:name](#get-usersusercommandsname)|Gets the command `:name` from `:user`
[PUT /users/:user/commands/:name](#put-usersusercommandsname)|Adds the command `:name` to `:user`
[PATCH /users/:user/commands/:name](#patch-usersusercommandsname)|Updates the command `:name` from `:user`
[DELETE /users/:user/commands/:name](#delete-usersusercommandsname)|Deletes the command `:name` from `:user`

## `GET /users/:user/commands`
Gets all commands for `:user`. Command variables will be masked without a valid [access token](../authentication.md) with scope `commands`.

#### Example Request
    GET https://api.nerdbot.tv/v3/users/test_user/commands
#### Example Response
    [
      {
        "name": "!test",
        "uses": 14,
        "allowFor": "subs",
        "text": "If you did this command, you are a subscriber."
      }
    ]

## `GET /users/:user/commands/:name`
Gets the command `:name` from `:user`. Command variables will be masked without a valid [access token](../authentication.md) with scope `manage_commands`.

#### Example Request
    GET https://api.nerdbot.tv/v3/users/test_user/commands/!test
#### Example Response
    {
      "name": "!test",
      "uses": 14,
      "allowFor": "subs",
      "text": "If you did this command, you are a subscriber."
    }

## `PUT /users/:user/commands/:name`
Adds the command `:name` to `:user`. Requires a valid [access token](../authentication.md) with scope `manage_commands`.

Parameter|Optional|Type|Description
---|---|---|---
text|no|string|The command's response
allowFor|no|string|Who can use the command (all/subs/mods)

#### Example Request
    PUT https://api.nerdbot.tv/v3/users/test_user/commands/!test2
          text=This is the second test
          &allowFor=all
#### Example Response
    {
      "name": "!test2",
      "uses": 0,
      "allowFor": "all",
      "text": "This is the second test"
    }

## `PATCH /users/:user/commands/:name`
Updates the command `:name` from `:user`. Requires a valid [access token](../authentication.md) with scope `commands`.

Parameter|Optional|Type|Description
---|---|---|---
text|yes|string|The command's response
allowFor|yes|string|Who can use the command (all/subs/mods)
uses|yes|int|The amount of times the command has been used

#### Example Request
    PATCH https://api.nerdbot.tv/v3/users/test_user/commands/!test2
            uses=1
#### Example Response
    {
      "name": "!test2",
      "uses": 1,
      "allowFor": "all",
      "text": "This is the second test"
    }

## `DELETE /users/:user/commands/:name`
Deletes the command `:name` from `:user`. Requires a valid [access token](../authentication.md) with scope `commands`.

#### Example Request
    DELETE https://api.nerdbot.tv/v3/users/test_user/commands/!test
> You will receive an empty body and a `204 No Content` response.
