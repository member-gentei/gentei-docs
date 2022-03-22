---
title: YouTube Permissions
---

One of the common comments about Gentei are that the permissions look kinda sketchy.

![oauth-permission](/assets/oauth-permissions.png)

The short response to that is this is unavoidable for the way that Gentei currently verifies memberships. I wish this could work with a less restrictive permission set, but I can at least explain why Gentei needs it.

# YouTube API permissions

The short, non-technical answer is that the app cannot ask for less permissions. YouTube/Google decided that the API used for Gentei's automatic membership checks must use these permissions. I wish I could ask for less!

In more technical detail: Gentei depends on reading out comment threads on a members-only video, and the associated YouTube Data API endpoint requires a specific OAuth permission scope called `https://www.googleapis.com/auth/youtube.force-ssl`.

Referencing that scope with [Google's table of all of their OAuth scopes](https://developers.google.com/identity/protocols/oauth2/scopes#youtube), this maps to the "See, edit, and permanently delete your YouTube videos, ratings, comments and captions" message that you'll see.

There's not really anything we can do about that past asking YouTube to reclassify this API endpoint under a separate OAuth scope and hope that it happens. `¯\_(ツ)_/¯`
