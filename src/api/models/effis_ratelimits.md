# EffisRatelimitConf Object

Represents a singular ratelimit for Effis (CDN). Unlike normal ratelimits, these also include a file size limit.

| Field           | Type   | Description                |
|-----------------|--------|----------------------------|
| reset_after     | Number | The number of seconds the client should wait before making new requests. |
| limit           | Number | The number of requests that can be made within the timeframe denoted by `reset_after`. |
| file_size_limit | String | The maximum total file size that can be requested in the timeframe denoted by `reset_after`. |


# EffisRatelimits Object

Represents the ratelimits for Effis. These ratelimits denote how often files can be requested from the CDN, as well as maximum filesize limits.

| Field          | Type                 | Description                |
|----------------|----------------------|----------------------------|
| assets         | EffisRatelimitConf   | The ratelimit information for the handling of Assets. |
| attachments    | EffisRatelimitConf   | The ratelimit information for the handling of Attachments. |


# Relevant Endpoints

| Method | Endpoint                                 |
|--------|------------------------------------------|
| GET    | [`/ratelimits`](../routes/ratelimits.md) |