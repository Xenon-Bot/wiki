---
title: API
description: Build custom features for Xenon and integrate it into your service
published: true
date: 2020-09-11T22:31:00.079Z
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
	"error": "You got ratelimited"
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
#### Query Parameters
