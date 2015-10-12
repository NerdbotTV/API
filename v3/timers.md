# Timers
Timers are an object owned by a [User](users.md).

Endpoint|Description
---|---
[GET /users/:user/timers](#get-usersusertimers)|Gets all timers for `:user`
[GET /users/:user/timers/:id](#get-usersusertimersid)|Gets the timer `:id` from `:user`
[POST /users/:user/timers](#post-usersusertimers)|Adds a timer for `:user`
[DELETE /users/:user/timers/:id](#delete-usersusertimersid)|Deletes the timer `:id` from `:user`

## `GET /users/:user/timers`
Gets all timers for `:user`. Timer variables will be masked without a valid [access token](../authentication.md) with scope `timers`.

#### Example Request
    GET https://api.nerdbot.tv/v3/users/test_user/timers
#### Example Response
    [
      {
        "id": 136,
        "text": "This is a test timer."
      }
    ]

## `GET /users/:user/timers/:id`
Gets the timer `:id` from `:user`. Timer variables will be masked without a valid [access token](../authentication.md) with scope `timers`.

#### Example Request
    GET https://api.nerdbot.tv/v3/users/test_user/timers/136
#### Example Response
    {
      "id": 136,
      "text": "This is a test timer."
    }

## `POST /users/:user/timers`
Adds a timer for `:user`. Requires a valid [access token](../authentication.md) with scope `timers`.

Parameter|Optional|Type|Description
---|---|---|---
text|no|string|The timer's text

#### Example Request
    POST https://api.nerdbot.tv/v3/users/test_user/timers
           text=This is the second test
#### Example Response
    {
      "id": 137,
      "text": "This is the second test"
    }

## `DELETE /users/:user/timers/:id`
Deletes the timer `:id` from `:user`. Requires a valid [access token](../authentication.md) with scope `timers`.

#### Example Request
    DELETE https://api.nerdbot.tv/v3/users/test_user/timers/136
> You will receive an empty body and a `204 No Content` response.
