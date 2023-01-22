# Pandemonium close codes

All Pandemonium intentional closes have a close code of `1011` the reasons however
can provide us with some additional info, here's a list of all the supported reasons:

- Client connection dead

> The client did not ping pandemonium for more than 45 seconds which resulted in
> a disconnection.

- Client hit rate limit

> The client surpassed their allowed connection and payload send rate limits which
> lead to them getting disconnected.

- Server error

> A server error has occurred ![A shrugging pepe](https://cdn.discordapp.com/emojis/951370278141841469.webp?size=16&quality=lossless)
