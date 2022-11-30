# Ratelimits

<span class=requestmethod><b>GET</b></span> `/ratelimits`

<!-- perhaps replace those with links? -->

Get the instance-specific ratelimits for Oprish (REST-api), Pandemonium (gateway), and Effis (CDN).


## Returns

The [InstanceRateLimits](../models/ratelimits.md) object for the connected Eludris instance.


## Errors

| Code | Description                                                    |
|------|----------------------------------------------------------------|
| 429  | Ratelimited; too many requests were made in a given timeframe. |