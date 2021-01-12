---
title: Settings
description: 
published: true
date: 2021-01-12T12:32:28.154Z
tags: xenon, premium, help
editor: markdown
dateCreated: 2020-10-06T13:12:14.120Z
---

# Permissions Settings
Change who is able to create backups, syncs & chatlog and load backups, chatlogs & templates. This does not affect basic commands like `x!ping`.

## Syntax

`x?settings permissions <level>`

## Arguments

# Tabs {.tabset}
## level

The permissions level that you want to set for this server.

`options: from, to, both` `required`

#### admins

Server admins can use all the relevant commands like `backup create`, `backup load` and `template load`.
**Bare careful with this!**

`x?settings permissions admins`

#### destructive owner *(default)*

Server admins can create backups but can't load a template or backup.

`x?settings permissions destructive owner`

#### owner

Server admins can neither create backups nor load a template or backup. Only the server owner can use any of the relevant commands.

`x?settings permissions destructive owner`

#### 

<br />