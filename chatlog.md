---
title: Chatlog
description: Chatlogs are used to save the last X messages in one channel. Like backups, chatlogs are linked to the creator account and can't be loaded by someone else.
published: true
date: 2025-09-14T23:50:29.019Z
tags: premium, help
editor: markdown
dateCreated: 2020-06-28T13:39:51.956Z
---

> All chatlog commands are only available for [premium](/premium) users.
{.is-info}

# Creating a chatlog

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

Please read [this](/en/help/attachment-limitations) if you are having issues loading messages with attached files.

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

# Deleting a chatlog

You obviously need to create chatlog before you can use this command.
You can find a list of your backups with `/chatlog list`.

> Deleting a chatlog is irreversible! Be careful with this command.
{.is-danger}

## Syntax

`/chatlog delete <chatlog_id>`

## Arguments

# Tabs {.tabset}
## backup_id

The id of the chatlog you want to delete. You get this after creating a chatlog.

`required`
