---
title: Import
description: Import data like channels, roles, emojis, stickers, etc. from JSON files
published: true
date: 2025-12-05T15:08:18.271Z
tags: 
editor: markdown
dateCreated: 2025-11-29T15:36:59.530Z
---

> Importing data is only available for [premium](/premium) users.
{.is-info}

# Import Server

Import the server settings, channels, and roles from the JSON file. Usually you get the JSON file after running `/export guild`.

You can also use AI tools like ChatGPT, Claude or Gemini to generate a JSON file. You can find some tips below.

## Syntax

`/import guild <json_file>`

## Arguments

# Tabs {.tabset}
## json_file
The JSON file containing the server data. This must follow the format [defined by Discord](https://discord.com/developers/docs/resources/guild#guild-object).

If you are using AI to generate the JSON file, make sure to explicitly tell it to follow the official Discord API format.

Example prompt:
```
Can you generate me the JSON code for a Discord server about GTA roleplay? 
Please follow the official Discord API specification for guild data.
```

**Files that don't follow the right format can't be imported and our team is not responsible for fixing them for you.**

<br />
