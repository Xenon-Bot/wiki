---
title: Backups
description: Backups are used to save and duplicate your server. Backups are limited to the user that created it, but not limited to a server. That means you can use backups to move, or duplicate a server.
published: true
date: 2021-05-17T13:31:24.324Z
tags: xenon, premium, help
editor: markdown
dateCreated: 2020-06-24T14:40:55.477Z
---

# Overview

Backups are used to save or duplicate your server. Backups are linked to the user that created it, but not limited to a server. That means you can use backups to move, or duplicate a server.
Backups can contain channels, roles, server settings and even messages, bans, nicknames and role assignments if you have [premium](/premium).

# Creating a backup
Create a backup of your discord. After the bot created the backup, it will tell you the backup id. You can find a list of your backups with x!backup list

> By default Xenon does not save messages, nicknames or role assignments. This is only possible with [Xenon Premium](/premium).
{.is-info}

## Syntax

`/backup create [message_count]`

## Arguments

# Tabs {.tabset}
## message_count

The count of messages to save per channel. Default is the max amount for your tier.

Only available for [premium](/premium) users!

`max: 0 / 25 / 100 / 250` `default: 0 / 25 / 100 / 250` `optional`

<br /><br />

# Loading a backup
Load a backup. You obviously need to create backup before you can use this command.

You can find a list of your backups with `x!backup list`.

> Loading a backup replaces all channels and roles in the discord. It does not kick the members.
{.is-warning}

## Syntax

`/backup load <backup_id> [message_count] [options]`

## Arguments

# Tabs {.tabset}
## backup_id

The id of the backup you want to load. 

You can get a list of your backups using `/backup list`.

`required`

## message_count

The count of messages to load per channel. Default is the max amount for your tier.

Only available for [premium](/premium) users!

`max: 0 / 25 / 100 / 250` `default: 0 / 25 / 100 / 250` `optional`

## options

A list of arguments, separated by a space. Putting a ! in front of the argument disables the option.
Only `settings`, `roles` and `channels` work for non-premium users.

`*` enables all

`!*` disables all

**Valid Arguments**: `settings members channels delete-channels roles delete-roles bans invite pins`

**Example**: `/backup load backup_id: 434ATZPVLA options: !* delete-roles roles` will only load roles
**Example**: `/backup load backup_id: 434ATZPVLA options: !delete-roles !channels` will load everything but not delete existing channels and roles

`optional` `default: delete-channels channels delete-roles roles settings`

<br /><br />

# Deleting a backup

You obviously need to create backup before you can use this command.

You can get a list of your backups using `/backup list`.

> Deleting a backup is irreversible! Be careful with this command.
{.is-warning}

## Syntax

`/backup delete <backup-id>`

## Arguments

# Tabs {.tabset}
## backup_id

The id of the backup you want to delete. 

You can get a list of your backups using `/backup list`.

`required`

<br /><br />

# Automated Backups / Interval

The bot can create a backup of your server in a certain interval. It overrides the old one every time it creates a new one. Different [premium tiers](https://wiki.xenon.bot/en/premium#xenon-tiers) can keep more than 1 interval backup per server.

To find your interval backups you can use `/backup list`. Look for the clock emoji next to the backup id.

## Syntax

`/backup interval on <interval> [message_count]`

## Arguments

# Tabs {.tabset}
## interval

The time between every backup.

[Premium](https://wiki.xenon.bot/en/premium#xenon-tiers) users can have this as low as 4h but free users have a minimum of 24 hours.

## message_count

The count of messages to save per channel. Default is the max amount for your tier.

Only available for [premium](/premium) users!

`max: 0 / 25 / 100 / 250` `default: 0 / 25 / 100 / 250` `optional`
