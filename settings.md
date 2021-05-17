---
title: Settings
description: 
published: true
date: 2021-05-17T13:40:56.265Z
tags: xenon, premium, help
editor: markdown
dateCreated: 2020-10-06T13:12:14.120Z
---

# Overview
Use the permission settings to change who is able to create backups, syncs & chatlog and load backups, chatlogs & templates. This does not affect basic commands like `/ping`.

## Syntax

`/settings permissions <level>`

## Arguments

# Tabs {.tabset}
## level

The permissions level that you want to set for this server.

#### Admins can use all commands

Server admins can use all the relevant commands like `backup create`, `backup load` and `template load`.
**Bare careful with this!**

`/settings permissions level: Admins can use all commands`

#### Admins can not take destructive actions *(default)*

Server admins can create backups but can't load a template or backup.

`/settings permissions level: Admins can not take destructive actions`

#### Only the owner can use the relevant commands

Server admins can neither create backups nor load a template or backup. Only the server owner can use any of the relevant commands.

`/settings permissions level: Only the owner can use the relevant commands`

#### 

<br />