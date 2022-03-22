---
title: Slash commands
---

# Slash commands

Most day-to-day interaction with Gentei happens via the `/gentei` slash command. All replies to this command are [ephemeral messages](https://support.discord.com/hc/en-us/articles/1500000580222-Ephemeral-Messages-FAQ) that are only visible to the user that ran the command.

## /gentei check

`/gentei check` allows users to trigger a membership check on-demand, which usually completes within a minute. This check is rate limited to mitigate abuse and only makes changes to roles that correspond to the current server.

![gentei check](/assets/slash-check.png)


## /gentei info

`/gentei info` allows users to check what roles are available in a server. 


## /gentei manage

`/gentei manage ...` contains subcommands that only administrators and the server owner can run.

### /gentei manage audit-set

`/gentei manage audit-set channel:#audit-channel` configures the bot to post any changes it makes to roles to `#audit-channel`.

The bot will try to post a test message to that channel, and if it doesn't work it will reply with the permissions that you need to grant to either the bot or the bot's role.

![gentei manage audit-set](/assets/slash-audit-set.png)

![gentei manage audit-set-example](/assets/slash-audit-set-example.png)

For more about the audit log format, please see the [Audit log](/bot/audit) documentation.

### /gentei manage audit-off

`/gentei manage audit-off` will disable audit logs from being sent to a previously configured channel.

![gentei manage audit-off](/assets/slash-audit-off.png)

### /gentei manage map

`/gentei manage map youtube-channel-id:UC... role:@members-only` maps a YouTube channel configured via the webapp to a role.

![gentei manage map](/assets/slash-map.png)

Before saving the role mapping, the bot will add and remove itself from the role to check that it has permissions. You can see this in the bot's own audit log, if you happen to have it enabled!

![manage map test](/assets/slash-map-audit.png)

### /gentei manage unmap

`/gentei manage unmap` can be run on either the role or YouTube channel ID to make Gentei stop managing a role.

![gentei manage unmap](/assets/slash-unmap.png)
