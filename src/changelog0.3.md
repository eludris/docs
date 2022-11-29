# Version 0.3 Changes

## API Changes

### Oprish API Changes

- Due to ratelimits being a / instance configurable thing, a new [`/ratelimits`
route](./api/routes/ratelimit.md) has been added besdies the already pre-existing
response headers.
- Ratelimit headers now also exist when you encounter a 429.
- The info route now has ratelimit.

### Pandemonium API Changes

- Changed the websocket CLOSE frame messages.
- The websocket connection now expects you to send a PING every 45 seconds as
opposed to 20 seconds.
- Switch to OPCode payloads instead of PING and PONG frames, also switched to
using a MESSAGE OPCode for new messages, refer to the [Pandemonium docs](./api/ws/payloads.md)
for more information.

### Effis API Changes

## Hosting

A new `Eludris.toml` file has been added which allows you to customise your instance,
from per route ratelimit data to the maximum message content length, all from
the convinience of one TOML file, check out the docs page about [configuring
your instance](./conf.toml) and the [`Eludris.toml` example in the github
repository](https://github.com/eludris/eludris/blob/next/Eludris.toml)

TODO: update the branch in the url to main after merge.

### Oprish Hosting Changes

- The `REDIS_URL` environment variable has been introduced as a direct way to
supply the url of your Redis/KeyDB instance as opposed to `ROCKET_DATABASES`.
