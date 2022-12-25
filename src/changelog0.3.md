# Version 0.3 Changes

## API Changes

### Oprish API Changes

- Due to ratelimits being a per instance configation thing, a new [`/ratelimits`
route](./oprish/ratelimits.md) has been added besdies the already pre-existing
response headers.
- Ratelimit headers now also exist when you encounter a 429 response.
- The [instance info](./oprish/instance_info.md) route now has ratelimit.

### Pandemonium API Changes

- Changed the websocket CLOSE frame messages.
- The websocket connection now expects you to send a PING every 45 seconds as
opposed to 20 seconds.
- Switch to OPCode payloads instead of `PING` and `PONG` frames, also switched to
using a `MESSAGE_CREATE` OPCode for new messages, refer to the [Pandemonium docs](./pandemonium/payloads.md)
for more information.

### Effis API Changes

Re-wrote the entirety of effis :D

Find out more in [Effis' documentation](./effis/index.md)

## Hosting

A new `Eludris.toml` file has been added which allows you to customise your instance,
from per route ratelimit settings to the maximum message content length, all from
the convinience of one TOML file, check out the docs page about [configuring
your instance](./conf.md) and the [`Eludris.toml` example in the github
repository](https://github.com/eludris/eludris/blob/main/Eludris.example.toml)

### Oprish Hosting Changes

- The `REDIS_URL` environment variable has been introduced as a direct way to
supply the url of your Redis/KeyDB instance as opposed to `ROCKET_DATABASES`.
