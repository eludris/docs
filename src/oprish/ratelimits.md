# Rate Limits

<span class=requestmethod><b>GET</b></span> `/ratelimits`

Get the ratelimit info for all of the instance's microservices, those being
[Oprish](./index.md), [Pandemonium](../pandemonium/index.md) and [Effis](../effis/index.md)

## Returns

The [InstanceRateLimits](../models/ratelimits.md) object for the Eludris instance.

## Example

```sh
curl \
  https://eludris.tooty.xyz/ratelimits
```
```json
{
  "oprish": {
    "info": {
      "reset_after": 5,
      "limit": 2
    },
    "message_create": {
      "reset_after": 5,
      "limit": 5
    },
    "ratelimits": {
      "reset_after": 5,
      "limit": 2
    }
  },
  "pandemonium": {
    "reset_after": 10,
    "limit": 5
  },
  "effis": {
    "assets": {
      "reset_after": 60,
      "limit": 5,
      "file_size_limit": 30000000
    },
    "attachments": {
      "reset_after": 120,
      "limit": 20,
      "file_size_limit": 100000000
    },
    "fetch_file": {
      "reset_after": 60,
      "limit": 30
    }
  }
}
```
