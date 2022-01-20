---
title: Authorization
description: ""
date: 2022-01-17T00:46:35.123Z
author:
  - "@rowanc1"
name: authorization
oxa: oxa:EplL6AlILV3RGEDPzj5U/RzBCtk3yOrXhAVY2z2Bw
---

# Authorization

+++ {"oxa":"oxa:EplL6AlILV3RGEDPzj5U/SDTL5gJ6vkR0x9HnWtNv.2","pinned":false}

Most translation and export functionality is local and does not require you to be logged into Curvenote. Additionally, the API for any public content on Curvenote does not require you to be authenticated. However, if you want to sync content from your private Curvenote projects to a local folder or write to any online projects you will need to be authenticated.

The Curvenote CLI works on an API token that can be generated from your personal settings on [curvenote.com](https://curvenote.com).

```{raw} html
<figure id="frGvUAfvAC" align="center">
  <div style="position: relative; display: inline-block; padding-bottom: 39%; width: 70%;">
    <iframe width="100%" height="100%" src="https://www.loom.com/embed/d4ae47586c9447649f934e892663b0ee" allowfullscreen="" allow="autoplay" style="width: 100%; height: 100%; position: absolute; top: 0px; left: 0px; border: none;"></iframe>
  </div>
</figure>
```

+++ {"oxa":"oxa:EplL6AlILV3RGEDPzj5U/Rw0HQbMsINo3BdJaFymK.2","pinned":false}

## Sign In to Curvenote

Once you have the API token, sign into the Curvenote CLI using the command:

```python
curvenote token set API_TOKEN
```

This will store a local config file that has your API token to be used for future calls to the library. You can also override the config path by having a `CURVENOTE_TOKEN` in your process environment, this is mostly helpful to use the Curvenote CLI from a continuous integration system or on a server.

```shell
export $CURVENOTE_TOKEN="API_TOKEN"
```

You can validate that you are signed in using the command:

```shell
curvenote auth list
```

This will print your username and email or tell you that you are not authenticated.

## Sign Out of Curvenote

To sign out of the Curvenote CLI, you can call:

```shell
curvenote token delete
```

This will remove the local config file with the API token in it. Note, if you have signed into the CLI using the environment variable, you can unset that using `unset CURVENOTE_TOKEN`. To confirm that you are logged out you can run the command `curvenote auth list` as before, and it should inform you that you are not authenticated.

+++ {"oxa":"oxa:EplL6AlILV3RGEDPzj5U/xu1lnGD1nQnVSnpoR0h2.2","pinned":false}

## User and Session Tokens

```{note}
**Note**: The below information is included for completeness, the CLI handles all session creation and token refresh if you use the user token created in the Curvenote API. 🎉
```

The user token that is provided by Curvenote is a signed JWT, that allows you to login and get a session token. The user token cannot be used for the API generally, instead a session token must be used. To get a session token, `POST` to the `/login` endpoint with an `Authorization` header that includes the user token provided by Curvenote; note that this URL is the audience field (`aud`) of the JWT. The response will validate your user token and provide a session token that can be used on any API endpoint. If you get a `401 Not Authorized` response from the server, your session token may have expired and you can use the above technique to refresh your session token.

