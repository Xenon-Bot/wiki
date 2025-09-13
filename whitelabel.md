---
title: Whitelabel
description: Whitelabel lets you customize the display name and icon of your bot in each server
published: true
date: 2025-09-13T17:50:17.195Z
tags: 
editor: markdown
dateCreated: 2025-09-13T17:39:58.654Z
---

> Customizing the appearance of the bot is only available for [premium](/premium) users.
{.is-info}

# Setting up Whitelabel

Create a chatlog of your channel. After the bot created the chatlog, it will tell you the chatlog id. You can find a list of your chatlogs with `/chatlog list`

## Syntax

`/chatlog create [message_count] [before]`

## Arguments

# Tabs {.tabset}
## message_count
The count of messages to save per channel. Default is the max amount for your tier.

`max: 0 / 250 / 500 / 1000` `default: 0 / 250 / 500 / 1000` `optional`

## before
A message id where to start fetching messages. Can be used to concatenate chatlogs.

`optional`

<br />

# Loading a chatlog

Load a chatlog. You obviously need to create chatlog before you can use this command.
You can find a list of your backups with `/chatlog list`.

> Loading a chatlog can take a long time. The bot might seem to pause multiple times during the process, this is normal.
{.is-info}

## Syntax

`/chatlog load <chatlog_id> [message_count]`

## Arguments

# Tabs {.tabset}
## chatlog_id
The id of the chatlog you want to load. You get this after creating a chatlog.

`required`

## message_count

The count of messages to load from the chatlog. Default is the max amount for your tier.

`max: 0 / 250 / 500 / 1000` `default: 0 / 250 / 500 / 1000` `optional`

<br />