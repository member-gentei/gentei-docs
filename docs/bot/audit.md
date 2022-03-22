---
title: Audit log
---

# Audit log

Gentei offers an enriched alternative to the built-in Discord audit log for role changes.

Using [`/gentei manage audit-set`](/bot/commands#/gentei-manage-audit-set), Gentei can be configured to send detailed audit log messages to a channel on the server.

![gentei manage audit-set-example](/assets/slash-audit-set-example.png)

As shown above, each role change that `gentei-bouncer#9835` makes will send an accompanying message with the following info:

* **Name**: the @mention of a user for easy reference. If a user leaves the server this becomes unusable, so the message also includes...
* **ID**: the universally unique Discord user ID.
* **Action**: the change made. This generally follows **Grant @role** or **Revoke @role**.
* **Timestamp**: a [formatted timestamp](https://discord.com/developers/docs/reference#message-formatting-timestamp-styles) of when the change was made. This may differ by a few seconds from Discord's built-in audit log - see below if you're curious.
* **Reason**: a human-readable explanation of why role membership changed for this user.

# Timestamp differences

The reason for differences between timestamps on Discord's audit log and the bot's audit log messages is very technical, but ultimately inconsequential.

On large Discord servers, which are generally classified as 5000+ users, role changes have been observed to follow [eventual consistency](https://en.wikipedia.org/wiki/Eventual_consistency). However, the Discord API sometimes accepts the role change API call but doesn't actually ever make the change.

There is unfortunately no way for the bot or any user to tell when a role change has *failed* to apply, so the bot will repeatedly make the API call every couple of seconds to change the role until the bot finally sees that it worked.

Thus, the audit message timestamp contains when the bot **observed the change**. The Discord audit log contains the timestamp for when the server **made the change**.

So if you see timestamp differences... congratulations? *Noblesse oblige*.
