# Commands
Commands are an object owned by a [User](users.md).

Endpoint|Description
---|---
[GET /users/:user/commands](#get-usersusercommands)|Gets all commands for `:user`
[GET /users/:user/commands/:name](#get-usersusercommandsname)|Gets the command `:name` from `:user`
[PUT /users/:user/commands/:name](#put-usersusercommandsname)|Adds the command `:name` for `:user`
[DELETE /users/:user/commands/:name](#delete-usersusercommandsname)|Deletes the command `:name` from `:user`

## `GET /users/:user/commands`
Gets all commands for `:user`. Command variables will be masked without a valid [access token](../authentication.md) with scope `manage_commands`.

#### Example Request
    GET https://api.nerdbot.tv/v2/users/test_user/commands
#### Example Response
    [
      {
        "id": 23,
        "name": "!test",
        "uses": 14,
        "allow_for": "subs",
        "response": "If you did this command, you are a subscriber."
      }
    ]

## `GET /users/:user/commands/:name`
Gets the command `:name` from `:user`. Command variables will be masked without a valid [access token](../authentication.md) with scope `manage_commands`.

#### Example Request
    GET https://api.nerdbot.tv/v2/users/test_user/commands/!test
#### Example Response
    {
      "id": 23,
      "name": "!test",
      "uses": 14,
      "allow_for": "subs",
      "response": "If you did this command, you are a subscriber."
    }

## `PUT /users/:user/commands/:name`
Adds the command `:name` for `:user`. Requires a valid [access token](../authentication.md) with scope `manage_commands`.

Parameter|Optional|Type|Description
---|---|---|---
response|no|string|The command's response
allow_for|no|string|Who can use the command (all/subs/mods)

#### Example Request
    PUT https://api.nerdbot.tv/v2/users/test_user/commands/!test2
          response=This is the second test
          &allow_for=all
#### Example Response
    {
      "id": 24,
      "name": "!test2",
      "uses": 0,
      "allow_for": "all",
      "response": "This is the second test"
    }

## `DELETE /users/:user/commands/:name`
Deletes the command `:name` from `:user`. Requires a valid [access token](../authentication.md) with scope `manage_commands`.

#### Example Request
    DELETE https://api.nerdbot.tv/v2/users/test_user/commands/!test
> You will receive an empty body and a `204 No Content` response.
