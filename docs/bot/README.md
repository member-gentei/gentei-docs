---
title: Discord bot
---

Gentei's batteries-included Discord bot is called **gentei-bouncer#9835**. The source code for the bot is available at (and deployed directly from) Gentei's [GitHub repository](https://github.com/member-gentei).

# Configuration

Configuration happens as part of the self-enrollment process on [https://gentei.tindabox.net](https://gentei.tindabox.net). Upon enrollment, the bot inviter and server owners initialize (or are added to) an access list of users that are allowed to run [`/gentei manage`](/bot/commands#/gentei-manage) commands.

Please see the [Roles and Enforcement](/bot/roles) page for details on how Gentei manages roles.


# Notes on operation + logging

The Discord bot is hooked up to [Google Cloud Operations](https://cloud.google.com/products/operations) for general logging and monitoring. Logs are kept for error alerting and auditing purposes and server-relevant logs can be provided to Discord server administrators on request.

Logs of Gentei's actions can also be retrieved via the Discord server audit log. Due to technical limitations, the bot cannot currently provide detailed audit reasons in the built-in Discord server audit log - but they do exist in both Google Cloud Operations and audit channel logs.

![](/assets/bot-audit-log.png)
