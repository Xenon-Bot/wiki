---
title: Sync
description: Sync messages between different channels and bans between different servers. It's possible to sync in one direction or in both.
published: true
date: 2025-10-14T13:39:48.624Z
tags: premium, help
editor: markdown
dateCreated: 2020-06-28T13:46:53.625Z
---

> All sync commands are only available for premium users.
{.is-info}

# Creating a message sync
Create a message sync between two channels in one or two directions. You can find a list of your syncs with `/sync list`

## Syntax

`/sync messages <direction> <channel>`

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

Create a ban sync between two guilds in one or two directions. You can find a list of your syncs with /sync list

## Syntax

`/sync bans <direction> <guild-id>`

# Tabs {.tabset}
## direciton

The direction for the sync. Either "from" to sync bans from the other guild to yours, "to" to sync bans from yours to the other channel or "both" for both directions.

`options: from, to, both` `required`

## guild-id

The id of the other guild. You can find out how to get a guild id [here](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-).

`required`

<br />

# Creating a role sync

Create a role sync between two roles in one or two directions. This way all members that have role A will also get role B or vice versa. Role A has to be on the server where you run the command, role B can also be on a different server.

You can find a list of your syncs with /sync list

## Syntax

`/sync roles <role_a> <direction> <server_b> <role_b>`

# Tabs {.tabset}
## role_a

The id of role A. You can find out how to get a role id [here](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-).

`required`

## direciton

The direction for the sync. Either "from" to sync assigned roles from the role B to role A, "to" to sync assigned roles from role A to the role B or "both" for both directions.

`options: from, to, both` `required`

## server_b

The id of the server that role B belongs to. You can find out how to get a guild id [here](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-).

`required`

## role_b

The id of role B. You can find out how to get a role id [here](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-).

`required`

<br />

# Deleting a sync

You obviously need to create sync before you can use this command.

You can find a list of your syncs with `/sync list`.

> Deleting a sync is irreversible! Be careful with this command.
{.is-danger}

## Syntax

`/sync delete <sync-id>`

## Arguments

# Tabs {.tabset}
## sync-id

The id of the sync you want to delete. You get this after creating a sync.

`required`