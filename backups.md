---
title: Backups
description: Backups are used to save and duplicate your server. Backups are limited to the user that created it, but not limited to a server. That means you can use backups to move, or duplicate a server.
published: true
date: 2021-01-12T12:29:49.410Z
tags: xenon, premium, help
editor: markdown
dateCreated: 2020-06-24T14:40:55.477Z
---

# Creating a backup
Create a backup of your discord. After the bot created the backup, it will tell you the backup id. You can find a list of your backups with x!backup list

> By default Xenon does not save messages, nicknames or role assignments. This is only possible with Xenon Premium.
{.is-warning}

## Syntax

`x!backup create [chatlog]`

## Arguments

# Tabs {.tabset}
## Chatlog

The count of messages to save per channel. Default is the max amount for your tier.

Only available for [premium](/premium) users!

`max: 0 / 25 / 100 / 250` `default: 0 / 25 / 100 / 250` `optional`

<br />

# Loading a backup
Load a backup. You obviously need to create backup before you can use this command.

You can find a list of your backups with `x!backup list`.

> Loading a backup replaces all channels and roles in the discord. It does not kick the members.
{.is-danger}

## Syntax

`x!backup load <backup-id> [chatlog] [options...]`

## Arguments

# Tabs {.tabset}
## backup-id

The id of the backup you want to load. You get this after creating a backup or using `x!backup list`.

`required`

## chatlog

The count of messages to load per channel 

Only available for [premium](/premium) users!

`max: 0 / 25 / 100 / 250` `default: 0` `optional`

## options

A list of arguments, separated by a space. Putting a ! in front of the argument disables the option.

`*` enables all

`!*` disables all

**Valid Arguments**: `settings members channels delete-channels roles delete-roles bans invite pins`

**Example**: `x!backup load <backup-id> !* delete-roles roles` will only load roles
**Example**: `x!backup load <backup-id> !delete-roles !channels` will load everything but not delete existing channels and roles

`optional` `default: members channels roles bans settings`

<br />

# Deleting a backup

You obviously need to create backup before you can use this command.

You can find a list of your backups with `x!backup list`.

> Deleting a backup is irreversible! Be careful with this command.
{.is-danger}

## Syntax

`x!backup delete <backup-id>`

## Arguments

# Tabs {.tabset}
## backup-id

The id of the backup you want to delete. You get this after creating a backup.

You can also use the guild id to delete the latest automated backup. 

`required`

<br />

# Automated Backups / Interval

The bot creates a backup of your guild in a certain interval. It overrides the old one every time it creates a new one. Different [premium tiers](https://wiki.xenon.bot/en/premium#xenon-tiers) can keep more than 1 interval backup.

To find your interval backups you can use `x!backup list`. Look for the clock emoji next to the backup id.

## Syntax

`x!backup interval <interval...> [chatlog]`

## Arguments

# Tabs {.tabset}
## interval

The time between every backup or "off".

Supported units: `hours(h)`, `days(d)`, `weeks(w)`

[Premium](https://wiki.xenon.bot/en/premium#xenon-tiers) users can have this as low as 4h but free users have a minimum of 1 day.

Examples: `1d`, `12h`

## chatlog

The count of messages to load per channel 

Only available for [premium](/premium) users!

`max: 0 / 25 / 100 / 250` `default: 0` `optional`
