# Instance Info

<span class=requestmethod><b>GET</b></span> `/`

Get information about the instance you're sending this request to.

Most of this data comes from the instance's configuration.

## Returns

The [InstanceInfo](../models/instance_info.md) object for the connected Eludris instance.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe. |
