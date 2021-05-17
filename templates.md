---
title: Templates
description: Xenon gives you access to hundreds of free templates. In contrast to backups, templates are public and can be used by everyone.
published: true
date: 2021-05-17T13:36:52.116Z
tags: xenon, premium, help
editor: markdown
dateCreated: 2020-06-26T16:25:21.365Z
---

# Overview
You can find a list of templates at [templates.xenon.bot](https://templates.xenon.bot). 
Most of them can be loaded on existing servers using Xenon or can be used to create new servers using the discord template feature. 
Some legacy templates are considered internal and can only be loaded using Xenon.

<br />

# Loading a template

Loading a template replaces all channels and roles in the discord. It does not kick the members.

You can also load any discord template in an **existing** server by supplying the template link, or supply the name to load one of Xenon's old templates.

## Syntax

`/template load <name_or_id> [options]`

## Arguments

# Tabs {.tabset}
## name_or_id

The name, id or link of the template you want to load.
e.g. `starter`, `6p9d4EBbuYcM` or `https://discord.new/6p9d4EBbuYcM`

`required`

## options

A list of arguments, separated by a space. Putting a `!` in front of the argument disables the option.

`*` enables all
`!*` disables all

**Valid Arguments**: `channels delete-channels roles delete-roles settings`

**Example**: `/template load name_or_id: r2uhQjNFKYHA options: !* delete-roles roles` will only load roles
**Example**: `/template load name_or_id: r2uhQjNFKYHA options: !delete-roles !channels` will load everything beside channels

`optional` `default: delete-channels channels delete-roles roles settings`


<br /><br />

# Creating a template

Create template of your server and put it on Xenon's [template list](https://templates.xenon.bot).

Head over to the server you want to create a template of, go to your server settings and look for the "Server Template" tab. Fill out all the required details. 

![createtemplate.png](/createtemplate.png)

> Quick reminder that all templates are public! Do not share share private information in templates.
{.is-danger}

## Adding to Xenon's template list

Click copy on the template link, and head over to [here](https://templates.xenon.bot/templates/add) and paste your template link in.

It should now be avaliable on the Xenon templates site.



