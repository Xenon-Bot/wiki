---
title: Sync
description: Sync messages between different channels and bans between different servers. It's possible to sync in one direction or in both.
published: true
date: 2021-01-12T12:32:09.536Z
tags: premium, help
editor: markdown
dateCreated: 2020-06-28T13:46:53.625Z
---

> All sync commands are only available for premium users.
{.is-info}

# Creating a message sync
Create a message sync between two channels in one or two directions. You can find a list of your syncs with `x?sync list`

## Syntax

`x?sync messages <direction> <channel>`

## Arguments

# Tabs {.tabset}
## direction

The direction for the sync. Either "from" to sync messages from the other channel to yours, "to" to sync messages from yours to the other channel or "both" for both directions.

`options: from, to, both` `required`

## channel

Either the channel id or mention of the other channel

`required`

<br />

# Creating a ban sync

Create a ban sync between two guilds in one or two directions. You can find a list of your syncs with x?sync list

## Syntax

`x?sync bans <direction> <guild-id>`

# Tabs {.tabset}
## direciton

The direction for the sync. Either "from" to sync bans from the other guild to yours, "to" to sync bans from yours to the other channel or "both" for both directions.

`options: from, to, both` `required`

## guild-id

The id of the other guild. You can find out how to get a guild id [here](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-).

`required`

<br />

# Deleting a sync

You obviously need to create sync before you can use this command.

You can find a list of your syncs with `x?sync list`.

> Deleting a sync is irreversible! Be careful with this command.
{.is-danger}

## Syntax

`x?sync delete <sync-id>`

## Arguments

# Tabs {.tabset}
## sync-id

The id of the sync you want to delete. You get this after creating a sync.

`required`