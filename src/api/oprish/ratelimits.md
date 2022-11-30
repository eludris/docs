# Ratelimits

<span class=requestmethod><b>GET</b></span> `/ratelimits`

Get the ratelimit info for all of the instance's microservices, those being
[Oprish](./oprish.md), [Pandemonium](../pandemonium/pandemonium.md) and [Effis]()

## Returns

The [InstanceRatelimits](../models/ratelimits.md) object for the Eludris instance.

## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe.  |
