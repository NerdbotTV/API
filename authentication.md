# Authentication
NerdBot uses OAuth2 for authentication. All requests follow the exact OAuth2 standards, but we'll still give some examples here.

## Making an app
To make authenticated requests, you must first [make an app](https://nerdbot.tv/api/apps/new).
Once you create an app, copy your client ID and generate a secret.
Make sure to copy the secret somewhere safe and **keep it private**.

|App Parameter|Description|
|---|---|
|Name|The name of your app, shown to users|
|Redirect URI|The URI users are redirected to when they authorize your app|

## Getting Authorized
To make requests on a user's behalf, you must get authorized by them.

### Authorization Code Flow
To use the Authorization Code Flow, follow these steps:

  1. Redirect the user to this URL:
  
        https://api.nerdbot.tv/oauth2/authorize
          ?response_type=code
          &client_id=[your app's client ID]
          &scope=[space-separated list of scopes]
    > We also support the `redirect_uri` parameter (must match your app's URI), and the `state` parameter (a random string you generate to prevent XSS).
    
    The page will ask the user to authorize or decline your app access.
  
  2. If the user authorizes your app, they will be redirected to:
  
        http://[your app's redirect URI]/?code=[authorization code]
        
  3. On your server, you must now make a request to:
  
        POST https://api.nerdbot.tv/oauth2/token
               client_id=[your app's client ID]
               &client_secret=[your app's client secret]
               &grant_type=authorization_code
               &code=[code received from authorization]
    > The `state` parameter is again supported here.
    
    The response, given a correct `code`, will be:
    
        {
          "access_token": "[access token for requests]",
          "scope": [requested scopes]
        }
        
  You may now use the access token to make [Authenticated Requests](#authenticated-requests).
  
### Implicit Grant Flow
To use the Implicit Grant Flow (e.g. for JavaScript-only apps), follow these steps:

  1. Redirect the user to this URL:
  
        https://api.nerdbot.tv/oauth2/authorize
          ?response_type=token
          &client_id=[your app's client ID]
          &scope=[space-separated list of scopes]
    > We also support the `redirect_uri` parameter (must match your app's URI).
    
    The page will ask the user to authorize or decline your app access.
    
  2. If the user authorizes your app, they will be redirected to:
  
        http://[your app's redirect URI]/#access_token=[authorization code]&scope=[requested scopes]
        
  You may now use the access token to make [Authenticated Requests](#authenticated-requests).
  
### Scopes (v3)
|Scope|Description|
|---|---|
info|View the user's email address, logs, and managers
manage|Edit bot options, enable/disable the bot
commands|Add, edit, and remove the user's commands
points|Manage the points of the user's viewers
songs|Add, delete, and manage the user's song requests
timers|Add, delete, and edit the user's timers


### Authenticated Requests
Once you have an access token, you may make authenticated requests on behalf of the user.
To do so, you can provide the token in two ways:

#### In the URI
    GET https://api.nerdbot.tv/v3?access_token=[token]

#### In the headers
    GET https://api.nerdbot.tv/v3
        Authorization: Bearer [token]