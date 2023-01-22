# Eludris Detailed

A detailed rundown and initial spec of how we *plan* Eludris to eventually function.

## Overview

The main goal with Eludris to provide a uniquely fresh but not entirely new experience. One where anyone can find (or create) a place focused around their interests while having a couple of fundemental policies that greatly improve users' experience.

These policies include being secure, 100% FOSS, privacy respecting and decentralised, while also not inconveniencing users who don't understand what these things entail, but still enhancing their experience.

In addition -- and as with anything Eludris-related -- modifying the source code or making your own clients, libraries, or tooling around Eludris is more than welcome and is in fact encouraged. We have an entire [GitHub organisation](https://github.com/eludris-community) focused on this.

## Takeaways

### You can make Communities.

Communities can be either message-based, post-based, or both.

Message-based communities work like how a Discord server does, having many different channels secluded to their own types. Members can -- as you can guess -- send messages within these channels.

Post-based communities work like how a Subreddit does with member being able to create different types of posts, vote on them and leave comments.

Both community types have shared features however, like roles, nicknames and so on.

Communities can be either public or private.

Communities can *usually* (depends on the instance) get manually reviewed by an instance admin to get verified if requested by the community's owner.

Verified communities can claim a namespace getting their own URL invite and are indexed onto list to be easily discoverable. However, doing so adds more restrictions upon them, such as no End-To-End-Encryption, stricter moderation, and so on.

### Accounts are unique.

Accounts for a **single** instance are unique, but when [federated](./federation#overview), this is broken.

You can follow people or send them friend requests.

You can also gain a Reddit Karma like form of point creatively called Social Credit by the Eludris Team, you gain it by getting more up-votes on your posts, spending time interacting with people, getting rewarded by instance moderators or through events.

### Bots are done right.

Bots will be user accounts like you'd see on Reddit or Twitter. They woun't have any bot-specific API limitations, however you have to set your bot as one for it to get verified.

Verification for bots only means that the bot and its owner will be given a little neat badge of honour.

Discord-styled application commands will be available. However unlike Discord they will not be forced upon people and will have more cool features, uses and will be more flexible. Additionally buttons and more message components will be available to give bot developers more room and tools to make cool stuff.

## Miscellaneous Info

### IDs

A Eludris ID is a 128 bit (16 byte) number, structured like so.

```
 12345678  12345678  12345678  12345678  12345678  12345678  12345678  12345678  12345678  12345678  12345678  12345678  12345678  12345678  12345678  12345678
 TTTTTTTT  TTTTTTTT  TTTTTTTT  TTTTTTTT  TTTTTTTT  TTTTTTTT  TTTTTTTT  TTTTTTTT  IIIIIIII  IIIIIIII  IIIIIIII  IIIIIIII  IIIIIIII  IIIIIIII  SSSSSSSS  SSSSSSSS
╰──────────────────────────────────────────────────────────────────────────────╯╰──────────────────────────────────────────────────────────╯╰──────────────────╯
                                       │                                                                     │                                       │
                                       │                                                                     │                          16 bit (2 byte) sequence.
                                       │                                                       48 bits (6 byte) Instance ID.
                        64 bit (8 byte) Unix timestamp.
```

T: A Unix timestamp with the Eludris epoch (1,650,000,000)─.

I: The id of the instance that generated this ID.

S: The sequence number of this ID

An instance ID is a 48 bit (6 byte) number, structured likes so.

```
 12345678  12345678  12345678  12345678  12345678  12345678  12345678 12345678
 TTTTTTTT  TTTTTTTT  TTTTTTTT  TTTTTTTT  TTTTTTTT  TTTTTTTT  TTTTTTTT TTTTTTTT
╰─────────────────────────────────────────────────────────────────────────────╯
                                       │
                                       │
                        48 bit (6 byte) Unix timestamp.
```

T: 48 bits of the current Unix timestamp (also with the Eludris) epoch.

### KeyDB

Eludris uses a non persistent KeyDB instance to store data that should be fetched with low latency and is ephemeral like rate-limit info.

Here's the structure of currently used keys:

- `rate_limit:<user-id>:<method>:<route>`

## How It Works

Eludris is split into 4 main parts, or well, microservices, these services are:

- Oprish: The Eludris RESTful API.
- Pandemonium: The Eludris websocket based gateway.
- Effis: The Eludris file server, proxy and CDN.
- Todel: The Eludris model and shared logic crate (which is not really a service but is agruably the most important component of Eludris).

All of the microservices' source code can be found in the [Eludris meta-repository](https://github.com/eludris/eludris).
