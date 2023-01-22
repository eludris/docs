# Eludris Detailed

A detailed rundown and initial spec of how we *plan* Eludris to eventually function.

## Overview

The main goal with Eludris to provide a uniquely fresh but not entirely new experience. One where anyone can find (or create) a place focused around their interests while having a couple of fundemental policies that greatly improve users' experience.

These policies include being secure, 100% FOSS, privacy respecting and decentralised, while also not inconveniencing users who don't understand what these things entail, but still enhancing their experience.

In addition -- and as with anything Eludris-related -- modifying the source code or making your own clients, libraries, or tooling around Eludris is more than welcome and is in fact encouraged. We have an entire [GitHub organisation](https://github.com/eludris-community) focused on this.

## Takeaways

### You can make Communities.

Communities can be either message-based, post-based, or both.

Message-based communities work like how a Discord server does, having many different channels secluded to their own types and members can -as you can guess- create messages within channels.

Post-based communities work like how a Subreddit does with member being able to create different types of posts, vote on them and leave comments.

Both community types have shared features however, like roles, nicknames and so on.

Communities can be either public or private.

Communities can *usually* (depends on the instance) get manually reviewed by an instance admin to get verified if requested by the community's owner.

Verified communities can claim a namespace getting their own URL invite and are indexed in a list to be easily discover-able, doing that however adds more restrictions upon them however (like no End-To-End-Encryption, stricter moderation and so on).

A community can get unverified at any point in time if they break the Eludris EULA, Terms of Service or instance rules, that however can be appealed and, unjustified unverification will (hopefully) not happen.

### Accounts are unique.

Accounts for a **single** instance are unique, but when [federated](./federation#overview), this is broken.

You can follow people or send them friend requests.

You can also gain a Reddit Karma like form of point creatively called Social Credit by the Eludris Team, you gain it by getting more up-votes on your posts, spending time interacting with people, getting rewarded by instance moderators or through events.

### Bots are done right.

Bots will be user accounts like you'd see on Reddit, or Twitter, which would mean that they wouldn't have any bot-specific API limitations, however you have to set your bot as one for it to get verified.

Verification for bots only means that the bot and it's owner will be given a little neat badge of honour.

Discord-styled application commands will be available, however unlike Discord they will not be forced upon people and will have more utilities, uses and will be more flexible, additionally buttons and more message components will be available to give bot developers more room and tools to make cool stuff.
