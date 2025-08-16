---
title: API
description: Build custom features for Xenon and integrate it into your service
published: true
date: 2025-08-16T12:53:16.800Z
tags: info
editor: markdown
dateCreated: 2020-08-29T09:28:00.964Z
---

# Intro
The API can be used to make existing or new services work together with Xenon. The goal of providing this API to other developers is to make the user experience as seamless as possible.
This API is at a very early stage and all endpoints are subject to change. (We will notify you before a breaking change happens)

API access is currently only given to very few people. Send `merlin.gg` a DM if you are interested in getting access.

Tokens have been granted to:
- [Wick](https://wickbot.com/)
- [Bender](https://benderbot.co)

# API Reference

All endpoints only accept and respond with a JSON body unless specifically stated.

Base Url: `https://xenon.bot/api`

## Rate Limits
There is currently no way to tell when you will hit a rate-limit. The api doesn't provide headers for that.
If the rate limit is exceeded, the API will return a 429 status code with a JSON body.
The JSON body contains a `retry_after` key which represents the number of milliseconds you should wait before making another request.
```json
{
	"error": "You got ratelimited",
	"retry_after": 5000.0
}
```

## Caching
Some endpoints cache the response to increase performance. Those endpoints will have the `Cache-Control` and `Expiration` headers set. You can use them to tell how long you can cache the data locally and reduce the load on our API.

## Authentication
Most endpoints require authentication using an internal bot token. These tokens are currently manually granted to very few people. Send `Merlin.gg` a DM if you are interested in getting access. 

The API looks for the token in the `Authorization` header. Unlike the discord-api, you don't have to prefix the token with "Bot".

## Endpoints

### ID Mappers `GET /mappers`

ID Mappers can be used to restore server specific settings after a backup was loaded. This endpoint will return an object containing all the ids that have changed. It can be used to translate IDs from the old server to the ids on the new one.

Might be used in a command like `!restore-settings <guild-id / backup-id>`.

To make sure that the user has permissions to restore settings from the specified guild, you should check the users permissions on that guild. If the guild no longer exists, you can make use of the `loaders` key. It contains the ids of the users that have loaded a backup with that guild combination before. This ensures that the user had at least admin on both servers at some point.

#### Tabs {.tabset}
##### Query Parameters

<table style="width:75%; text-align:center; margin-left:auto;margin-right:auto;">
<thead>
  <tr>
    <th>Key</th>
    <th>Description</th>
    <th>Required</th>
    <th>Default</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>source</td>
    <td>ID of the guild where the user wants to restore the settings from (Where the backup was created) (Supplied by the user)</td>
    <td>either "source" or "backup"</td>
    <td>-</td>
  </tr>
    <tr>
    <td>target</td>
    <td>ID of the guild where the user wants to restore the settings on (Where the backup was loaded) (Most likely where the command was executed)</td>
    <td>yes</td>
    <td>-</td>
  </tr>
    <tr>
    <td>backup</td>
    <td>ID of the backup that was loaded (Supplied by the user)</td>
    <td>either "source" or "backup"</td>
    <td>-</td>
  </tr>
</tbody>
</table>

##### JSON Body
This endpoint doesn't accept a body

##### JSON Response

<table style="width:75%; text-align:center; margin-left:auto;margin-right:auto;">
<thead>
  <tr>
    <th>Key</th>
    <th>Description</th>
    <th>Always Returned</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>ids</td>
    <td>Object of "old-id" -> "new-id"</td>
    <td>yes</td>
  </tr>
    <tr>
    <td>loaders</td>
    <td>List of users that loaded backups with this guild combination (used for permission checks)</td>
    <td>no</td>
  </tr>
</tbody>
</table>

##### Example

__Url__
`GET /mappers?target=496683369665658880&source=410488579140354049`

__JSON Body__
```json
{}
```

__JSON Response__
```json
{
    "source_id": "410488579140354049",
    "target_id": "496683369665658880",
    "ids": {
        "410488579140354049": "496683369665658880",
        "410520361789161472": "754098965649162251",
        "410533472055066624": "754098969658916895",
        "410534436191469570": "754098966760652860",
        "419932531828457473": "754098968748752987",
        "422869735714324499": "754098972716695573",
        "424288090316603418": "754098973509288008",
        "443833570046509057": "754098971030323321",
        "451843816484372480": "754098964390740016",
        "480435337303425025": "754098970627670056",
        "484796812851413012": "754098976092848220",
        "493698045465067530": "754098971881898206"
    },
    "loaders": [
        "386861188891279362"
    ]
}
```


### Loader Events `WS /loaders/ws`

Receive live updates about currently running loaders. Loaders can both be templates or backups.
Listening for the "done" event could be useful to restore server specific settings automatically after a backup / template was loaded. The content of the event may differ but will always include enough information to query the id mapper.

There are three types of events: start (a loader was started), status (loader status updated), 
done (loader has finished).
Status updates are limited to 1/5s/loader, so it's not guaranteed that you receive all status events. The status strings (e.g. "loading roles") are internal values and might change at any time.
You should always receive the "start" and "done" events.

The Authorization header must be sent with the initiating HTTP request.

#### Tabs {.tabset}
##### Query Parameters
This endpoint doesn't accept query parameters.

##### WS Send
The websocket doesn't require you to send any information.

##### WS Receive

<table style="width:75%; text-align:center; margin-left:auto;margin-right:auto;">
<thead>
  <tr>
    <th>Key</th>
    <th>Description</th>
    <th>Always Returned</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>event</td>
    <td>The loader event ("start", "done" or "status")</td>
    <td>yes</td>
  </tr>
    <tr>
    <td>data</td>
    <td>
      <table style="width:75%; text-align:center; margin-left:auto;margin-right:auto;">
        <thead>
          <tr>
            <th>Key</th>
            <th>Description</th>
            <th>Always Returned</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>id</td>
            <td>The guild-id where the loader is running</td>
            <td>yes</td>
          </tr>
          <tr>
            <td>type</td>
            <td>The type of the loader ("backup" or "template")</td>
            <td>in "start" & "done"</td>
          </tr>
          <tr>
            <td>user_id</td>
            <td>The id of the user that is loading the backup or template)</td>
            <td>in "start" & "done"</td>
          </tr>
          <tr>
            <td>source_id</td>
            <td>The guild-id where the template / backup was created</td>
            <td>in "start" & "done"</td>
          </tr>
          <tr>
            <td>backup_id</td>
            <td>The backup-id that is being loaded</td>
            <td>if type = "backup"</td>
          </tr>
          <tr>
            <td>template_id</td>
            <td>The template-id that is being loaded</td>
            <td>if type = "template"</td>
          </tr>
          <tr>
            <td>status</td>
            <td>The loader status</td>
            <td>in "status"</td>
          </tr>
        </tbody>
      </table>
    </td>
    <td>yes</td>
  </tr>
</tbody>
</table>

##### Example

__Url__
`WS /loaders/ws`

__WS Send__
```json
{}
```

__WS Receive__
```json
{
  "event": "start", 
  "data": {
    "id": "756891586859892777", 
    "type": "backup", 
    "user_id": "386861188891279362",
    "source_id": "670235515903279105", 
    "backup_id": "3zydfwqp0h"
  }
}
```
```json
{
  "event": "status", 
  "data": {
    "id": "756891586859892777",
    "status": "deleting roles"
  }
}
```
```json
{
  "event": "status", 
  "data": {
    "id": "756891586859892777",
    "status": "deleting channels"
  }
}
```
```json
{
  "event": "status", 
  "data": {
    "id": "756891586859892777",
    "status": "loading roles"
  }
}
```
```json
{
  "event": "status", 
  "data": {
    "id": "756891586859892777",
    "status": "loading channels"
  }
}
```
```json
{
  "event": "done", 
  "data": {
    "id": "756891586859892777", 
    "type": "backup", 
    "user_id": "386861188891279362",
    "source_id": "670235515903279105", 
    "backup_id": "3zydfwqp0h"
  }
}
```

### Attach bot to templates `POST /templates/{template_id}/bots`

Add your bot to the list of bots that include settings for that template. This will make your bot show up on the template details page and should only be used if you are able to restore bot settings for that template.

This can work by both listening to the DONE loader event (for servers that your bot is already on) and by providing a command for users that add your bot after loading the template.

#### Tabs {.tabset}
##### Query Parameters
This endpoint doesn't accept query parameters.

##### JSON Body

<table style="width:75%; text-align:center; margin-left:auto;margin-right:auto;">
<thead>
  <tr>
    <th>Key</th>
    <th>Description</th>
    <th>Required</th>
    <th>Default</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>user</td>
    <td>ID of the user that your bot is acting in behalf of. (e.g. the user that ran the command) This can be used as a simple permission check and has to match the template creator.</td>
    <td>no</td>
    <td>-</td>
  </tr>
</tbody>
</table>

##### JSON Response

Empty json object on success.

##### Example

__Url__
`POST /templates/hHGhNE6wyxgF/bots`

__JSON Body__
```json
{"user": "647737109494497281"}
```

__JSON Response__
```json
{}
```

### Detach bot from templates `DELETE /templates/{template_id}/bots`

Delete your bot from the list of bots that include settings for that template.
Same behavior as `POST /templates/{template_id}/bots`.


