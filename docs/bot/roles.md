---
title: Roles and Enforcement
---

# Gentei-managed roles

Gentei-managed roles are roles that Gentei establishes sole membership control over. Establishing exclusive control over this role is important because it keeps role management as simple as possible, which in turn prevents confusion about why someone does or does not have a role.

Put another way, Gentei regularly overwrites the entire role membership list with its own, internal list of which users should have this role.

{% info Vocabulary note %}
For the rest of this page, "role" will only ever refer to a Gentei-managed role.
{% end %}

# Enforcement

Gentei performs role enforcement *about* once a day to maintain role mapping integrity. 

In general, the bot is told to enforce roles at the end of a daily job that performs membership checks for all users. As of 2022/03/21, this job starts around ~1PM Pacific Time.

## Process walkthrough

When told to enforce roles, the bot goes through all of the non-disabled roles that it has configured. (Enforcement for a role is disabled when membership checks are disabled for the corresponding YouTube channel.)

For each user that holds the role:

1. If a user is not registered with Gentei, the user is removed from the role.
1. If a user is registered with Gentei and failed a membership check...
   1. ...within the role's grace period, no  changes are made. The user will be DM'd about the check failure to give them an opportunity to renew their membership. (the default grace period is 1 calendar day)
   1. ...past the role's grace period, the user is removed from the role if the user has the role. 

For each Gentei-registered user in the Discord server that does not have the role:

1. If the user passed a membership check, they are granted the role.

## Grace period

{% info Coming soon %}
Configurable grace periods and membership loss warnings are not yet implemented, and all roles currently use the default setting of 1 calendar day. Please treat this section as a proposal and feel free to leave feedback in the `#gentei-限定` channel!
{% end %}

Grace periods allow users that currently hold roles to fail checks for a certain period of time. The only unit of time that can be configured is a calendar day, and each calendar day aligns to UTC timezone.

Admins/mods can configure grace periods that are more/less strict than the default of **1 calendar day**. 

### Calendar day behavior

Calendar day grace periods are best explained by example. For example, say that a user has verified their last day of membership for a channel at 23:59 UTC on January 1. This channel is mapped to 2 different verified membership roles that this user holds:

* `@Smol` - with the default grace period of 1 day.
* `@Long` - with a grace period of 7 days.

On January 2, this user fails a membership check because January 1 was their last day. Gentei does not make any changes, but stores the first day that the check failed. When the bot performs role enforcement on January 2, it will DM this user about losing their membership to `@Smol` tomorrow if a check on January 3 fails.

On January 3, this user fails a membership check again. When the bot performs role enforcement on January 3, it removes this user from the `@Smol` role.

On January 8 - on the 7th day of the grace period for `@Long` - the bot will DM this user about losing their membership to `@Long` tomorrow.

On January 9, this user loses their membership to `@Long` during role enforcement.


## User lifecycle notes

In response to behavior that confused both users and Discord moderation teams in v1, v2's user deletion process now immediately removes Gentei-managed roles from deleted users. The bot then attempts to DM the user to confirm account deletion, but proceeds with deletion regardless.
