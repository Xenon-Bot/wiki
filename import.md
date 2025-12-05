---
title: Import
description: Import data like channels, roles, emojis, stickers, etc. from JSON files
published: true
date: 2025-12-05T14:54:19.569Z
tags: 
editor: markdown
dateCreated: 2025-11-29T15:36:59.530Z
---

> Importing data is only available for [premium](/premium) users.
{.is-info}

# Import Server

Import the server settings, channels, and roles from the JSON file. Usually you get the JSON file after running `/export guild`.

## Syntax

`/import guild <json_file>`

## Arguments

# Tabs {.tabset}
## json_file
The JSON file containing the server data. This must follow the format [defined by Discord](https://discord.com/developers/docs/resources/guild#guild-object).

If you are using AI to generate the JSON file, make sure to explicitly tell it to follow the official Discord API format.

**Files that don't follow the right format can't be imported and our team is not responsible for fixing them for you.**

<br />
