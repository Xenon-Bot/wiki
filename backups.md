---
title: Backups
description: Backups are used to save and duplicate your server. Backups are limited to the user that created it, but not limited to a server. That means you can use backups to move, or duplicate a server.
published: true
date: 2020-07-14T12:30:57.332Z
tags: xenon, support
editor: markdown
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

The count of messages to save per channel

Only available for [premium](/premium) users!

> Backups are not allowed to exceed a maximum size of 16 Megabyte. This might be a limitation for very large servers with a lot of channels and messages.
{.is-warning}

`max: 0 / 25 / 100 / 250` `default: 0` `optional`

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

The id of the backup you want to load. You get this after creating a backup.

You can also use the guild id to load the latest automated backup. 

`required`

## chatlog

The count of messages to load per channel 

Only available for [premium](/premium) users!

`max: 0 / 25 / 100 / 250` `default: 0` `optional`

## options

A list of arguments, separated by a space. Putting a ! in front of the argument disables the option.

`*` enables all

`!*` disables all

**Valid Arguments**: `members channels roles bans settings`

**Example**: `x!backup load <backup-id> !* roles will only load roles`

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

The bot creates a backup of your guild in a certain interval. It overrides the old one every time it creates a new one. 

To load a automated backup you can use `x!backup load interval` to load the last automated backup from the current guild or `x!backup load <guild_id>` to load the last automated backup from an other guild.

## Syntax

`x!backup interval <interval...> [chatlog]`

## Arguments

# Tabs {.tabset}
## interval

The id of the backup you want to delete. You get this after creating a backup.

You can also use the guild id to delete the latest automated backup. 

## chatlog

The count of messages to load per channel 

Only available for [premium](/premium) users!

`max: 0 / 25 / 100 / 250` `default: 0` `optional`
