# Fetch static file

<span class=requestmethod><b>GET</b></span> `/static/<name>`

Fetch the static file with the provided name. Static files are added by the instance owner and cannot be externally modified.


## Returns

The static file with the provided name. This is returned with header `Content-Disposition: inline` set.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |




# Download static file

<span class=requestmethod><b>GET</b></span> `/static/<name>/download`

Download the static file with the provided name.


## Returns

The static file with the provided name. This is returned with header `Content-Disposition: attachment` set.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |
