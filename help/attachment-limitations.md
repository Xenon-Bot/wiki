---
title: Message Attachment Limitations
description: Limitations to backing up and restoring message attachments / attached files
published: true
date: 2025-10-30T08:37:16.932Z
tags: 
editor: markdown
dateCreated: 2025-09-14T23:44:24.325Z
---

> Backing up and restoring message attachments is only available to [premium](/premium) users.
{.is-info}

When backing up and restoring message attachments there are some limitations enforced by Discord. This is because Xenon can't actually store the files, it only stores a link to each attachment.

Message attachments include any images, videos, or other files that are sent in a Discord message.

- Message attachments can only be restored if the **backup is less than 24 hours old**
- Message attachments can only be restored if the **original messages still exist**
- Message attachments can only be restored if the combined **size of files in one message is less than 8MB**

If you are looking for a solution that actually stores the message attachments and can restore them even if the backup is older than 24 hours or the original messages have been deleted, please check out [Xenon Vault](https://vault.xenon.bot).