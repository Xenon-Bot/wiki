---
title: API
description: Build custom features for Xenon and integrate it into your service
published: true
date: 2020-09-11T22:44:17.239Z
tags: 
editor: markdown
---

# Intro
The API can be used to make existing or new services work well together with Xenon. The goal of providing this API to other developers is to make the user experience as seamless as possible.
This API is at a very early stage and all endpoints are subject to change. (We will notify you before a breaking change happens)

API access is currently only given to very few people. Send `Merlin#1337` a DM if you are interested in getting access.

# API Reference

All endpoints only accept and respond with a JSON body unless specifically stated.

Base Url: `https://xenon.bot/api`

## Rate Limits
There is currently no way to tell when you will hit a rate-limit. The api doesn't provide headers for that.
In the case that a rate limit is exceeded, the API will return a 429 status code with a JSON body.
The JSON body contains a `retry_after` key which represents the number of milliseconds you should wait before making another request.
```json
{
	"error": "You got ratelimited",
  "retry_after": 5000.0
}
```

## Caching
Some endpoints cache the response to increase performance. Those endpoints will have the `Cache-Control` and `Expiration` headers set. You can use them to tell you can cache the data locally and reduce the load on our API.

## Authentication
Currently all edpoints require authentication using an internal bot token. These tokens currently are manually granted to very few people. Send `Merlin#1337` a DM if you are interested in getting access. 

The API looks for the token in the `Authorization` header. Unlike the discord-api, you don't have to prefix the token with "Bot ".

## Endpoints

### ID Mappers `GET /backups/ids`

# Tabs {.tabset}
## Query Parameters

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
    <td>ID of the guild where the user wants to restore the settings from (Where the backup was created) (supplied by the user)</td>
    <td>either "source" or "backup"</td>
    <td>-</td>
  </tr>
    <tr>
    <td>target</td>
    <td>ID of the guild where the user wants to restore the settings on (Where the backup was loaded) (probably where the command was executed)</td>
    <td>yes</td>
    <td>-</td>
  </tr>
    <tr>
    <td>backup</td>
    <td>ID of the backup that was loaded (supplied by the user)</td>
    <td>either "source" or "backup"</td>
    <td>-</td>
  </tr>
</tbody>
</table>

## JSON Body
This body doesn't accept a body

## JSON Response

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

## Example

Url:
`GET /backups/ids?target=496683369665658880&source=410488579140354049`

JSON Body:
```json
{}
```

JSON Response:
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



