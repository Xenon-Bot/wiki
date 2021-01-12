---
title: Chatlog
description: Chatlogs are used to save the last X messages in one channel. Like backups, chatlogs are linked to the creator account and can't be loaded by someone else.
published: true
date: 2021-01-12T12:31:51.071Z
tags: premium, help
editor: markdown
dateCreated: 2020-06-28T13:39:51.956Z
---

> All chatlog commands are only available for [premium](/premium) users.
{.is-info}

# Creating a chatlog

Create a chatlog of your channel. After the bot created the chatlog, it will tell you the chatlog id. You can find a list of your chatlogs with `x?chatlog list`

## Syntax

`x?chatlog create [count]`

## Arguments

# Tabs {.tabset}
## Count
The count of messages to save per channel 

`max: 0 / 250 / 500 / 1000` `default: 250` `optional`

<br />

# Loading a chatlog

Load a chatlog. You obviously need to create chatlog before you can use this command.
You can find a list of your backups with `x?chatlog list`.

> Loading a chatlog can take a long time. The bot might seem to pause multiple times during the process, this is normal.
{.is-info}

## Syntax

`x?chatlog load <chatlog-id> [count]`

## Arguments

# Tabs {.tabset}
## chatlog-id
The id of the chatlog you want to load. You get this after creating a chatlog.

`required`

## count

The count of messages to load from the chatlog 

`max: 0 / 250 / 500 / 1000` `default: 250` `optional`

<br />

# Deleting a chatlog

You obviously need to create chatlog before you can use this command.
You can find a list of your backups with `x?chatlog list`.

> Deleting a chatlog is irreversible! Be careful with this command.
{.is-danger}

## Syntax

`x?chatlog delete <chatlog-id>`

## Arguments

# Tabs {.tabset}
## backup-id

The id of the chatlog you want to delete. You get this after creating a chatlog.

`required`
