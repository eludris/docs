# Rate Limits

Rate limits in Eludris fully depend on the instance's configuration, you can always
get a specific instance's ratelimit info by using the [`/ratelimit`](../oprish/ratelimits.md)
route, response headers also exist.

## RateLimitConf

Represents a ratelimit for a specific part of the Eludris spec.

| Field       | Type   | Description |
|-------------|--------|-------------|
| reset_after | Number | The number of seconds the client should wait before making new requests.
| limit       | Number | The number of requests that can be made within the timeframe denoted by `reset_after`. |

### Example

```json
{
  "reset_after": 10,
  "limit": 5
}
```

## InstanceRateLimits

Represents all ratelimits that apply to the connected Eludris instance. This includes
individual ratelimit information for Oprish (REST-api), Pandemonium (Gateway), and Effis (CDN).

| Field       | Type   | Description |
|-------------|--------|-------------|
| oprish      | [OprishRateLimits](./oprish_ratelimits.md) | The ratelimits that apply to the connected Eludris instance's REST api. |
| pandemonium | RateLimitConf | The ratelimits that apply to the connected Eludris instance's gateway. |
| effis       | [EffisRateLimits](./effis_ratelimits.md) | The ratelimits that apply to the connected Eludris instance's CDN. |

## OprishRateLimits

Represents the ratelimits for Oprish (REST-api). This denotes the ratelimits on
each individual route.

| Field          | Type              | Description                |
|----------------|-------------------|----------------------------|
| info           | [RateLimitConf](./ratelimits.md) | The ratelimit information for the [/](../oprish/instance_info.md) route. |
| message_create | [RateLimitConf](./ratelimits.md) | The ratelimit information for the [/messages](../oprish/messages/create.md) route. |
| ratelimits     | [RateLimitConf](./ratelimits.md) | The ratelimit information for the [/ratelimits](../oprish/ratelimits.md) route. |

## EffisRateLimitConf Object

Represents a singular ratelimit for Effis (CDN). Unlike normal ratelimits, these
also include a file size limit.

| Field           | Type   | Description |
|-----------------|--------|-------------|
| reset_after     | Number | The number of seconds the client should wait before making new requests. |
| limit           | Number | The number of requests that can be made within the timeframe denoted by `reset_after`. |
| file_size_limit | Number | The maximum number of bytes that can be uploaded in the timeframe denoted by `reset_after`. |

### Example

```json
{
  "reset_after": 10,
  "limit": 5,
  "file_size_limit": 50000000 // 50MB
}
```

## EffisRateLimits Object

Represents the ratelimits for Effis. These ratelimits denote how often files can
be requested from the CDN, as well as maximum filesize limits.

| Field          | Type                 | Description |
|----------------|----------------------|-------------|
| assets         | EffisRateLimitConf   | The ratelimit information for the handling of Assets. |
| attachments    | EffisRateLimitConf   | The ratelimit information for the handling of Attachments. |

## Relevant Endpoints

| Method | Endpoint |
|--------|----------|
| GET    | [`Oprish /ratelimits`](../oprish/ratelimits.md) |
