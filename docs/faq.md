---
title: FAQ
---

Some frequently asked questions are posted here.

## Why doesn't Gentei support membership tenure or tiers?

Membership tenure and level information (e.g. member for 6 months or a "tier 2" member) is not available via the YouTube API from the channel member's end. 

It is however available for the target/monetized YouTube channel in the [members.list](https://developers.google.com/youtube/v3/docs/members/list) API call, which is likely how Discord's official [YouTube Channel Memberships integration](https://support.discord.com/hc/en-us/articles/215162978-Youtube-Channel-Memberships-Integration-FAQ) works. Discord however does not use tier or tenure information for role assignment.

## How does Gentei pick members-only videos for verification?

A video is randomly chosen from the unlisted playlist of membership videos that YouTube maintains for each channel that has membership monetization enabled. 

This process is likely to cause issues with checking YouTube memberships against tier-restricted videos, (e.g. Gentei may randomly pick a Tier 3 video, so anyone with Tier 1 + 2 can't verify) so please reach out to me to set the membership check video ID manually.

Gentei cannot automatically detect or work around this issue, so manual intervention is required in every case.

## Can I use Gentei for free... and for commercial use?

Yes! As (probably) the first members-only verification bot in the vtuber community, Gentei was a [pro bono](https://en.wikipedia.org/wiki/Pro_bono) effort to help create an online space for members-only discussion outside of streams and comment sections.

I'll post in `#gentei-announce` and edit the text of this question if that changes. Feel free to DM me via Discord or Twitter if you have any questions about that.

## How do I contact you?

The best way to do so is by posting in the `#gentei-限定` channel in the [Hololive Creators Club Discord](https://discord.gg/xJd9De).

If you're a server moderator/owner/admin using Gentei, consider following the `#gentei-announce` channel to receive comms about new features, disruptions, and other announcement-worthy stuff.

If you would prefer to reach out privately, feel free to DM `のヮの#6969` over Discord as well.
