---
title: Backups
description: Backups are used to save and duplicate your server. Backups are limited to the user that created it, but not limited to a server. That means you can use backups to move, or duplicate a server.
published: true
date: 2020-06-24T16:10:44.987Z
tags: xenon, support
editor: markdown
---

# Creating a backup
Create a backup of your discord. After the bot created the backup, it will tell you the backup id. You can find a list of your backups with x!backup list

> By default Xenon does not save messages, nicknames or role assignments. This is only possible with Xenon Premium.
{.is-warning}

<br />

## Syntax

`x!backup create [chatlog]`

<br />

## Arguments

# Tabs {.tabset}
## Chatlog

The count of messages to save per channel

Only available for [premium](/premium) users!

`max: 0 / 25 / 100 / 250` `default: 0` `optional`

<br />

# Loading a backup
Load a backup. You obviously need to create backup before you can use this command.

You can find a list of your backups with `x!backup list`.

> Loading a backup replaces all channels and roles in the discord. It does not kick the members.
{.is-danger}

<br />

## Syntax

`x!backup load <backup-id> [chatlog] [options...]`

<br />

## Arguments

# Tabs {.tabset}
## backup-id

The id of the backup you want to load. You get this after creating a backup.

You can also use the guild id to load the latest automated backup. 

`required`

<br />

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
