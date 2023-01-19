# Rate Limits

Rate limits in Eludris fully depend on the instance's configuration. You can always
get a specific instance's ratelimit info by using the [`/rate_limit`](../oprish/rate_limits.md)
route or dynamically using response headers.

## RateLimitConf

Represents a rate limit for a specific part of the Eludris spec.

| Field       | Type   | Description                                                                             |
| ----------- | ------ | --------------------------------------------------------------------------------------- |
| reset_after | Number | The number of seconds the client should wait before making new requests.                |
| limit       | Number | The number of requests that can be made within the time frame denoted by `reset_after`. |

### Example

```json
{
  "reset_after": 10,
  "limit": 5
}
```

## InstanceRateLimits

Represents all rate limits that apply to the connected Eludris instance. This includes
individual rate limit information for Oprish (REST-api), Pandemonium (Gateway), and Effis (CDN).

| Field       | Type                                        | Description                                                              |
| ----------- | ------------------------------------------- | ------------------------------------------------------------------------ |
| oprish      | [OprishRateLimits](./oprish_rate limits.md) | The rate limits that apply to the connected Eludris instance's REST api. |
| pandemonium | RateLimitConf                               | The rate limits that apply to the connected Eludris instance's gateway.  |
| effis       | [EffisRateLimits](./effis_rate limits.md)   | The rate limits that apply to the connected Eludris instance's CDN.      |

## OprishRateLimits

Represents the rate limits for Oprish (REST-api). This denotes the rate limits on
each individual route.

| Field          | Type                              | Description                                                                         |
| -------------- | --------------------------------- | ----------------------------------------------------------------------------------- |
| info           | [RateLimitConf](./rate_limits.md) | The rate limit information for the [/](../oprish/instance_info.md) route.           |
| message_create | [RateLimitConf](./rate_limits.md) | The rate limit information for the [/messages](../oprish/messages/create.md) route. |
| rate limits    | [RateLimitConf](./rate_limits.md) | The rate limit information for the [/rate_limits](../oprish/rate_limits.md) route.  |

## EffisRateLimitConf Object

Represents a singular rate limit for Effis (CDN). Unlike normal rate limits, these
also include a file size limit.

| Field           | Type   | Description                                                                                  |
| --------------- | ------ | -------------------------------------------------------------------------------------------- |
| reset_after     | Number | The number of seconds the client should wait before making new requests.                     |
| limit           | Number | The number of requests that can be made within the time frame denoted by `reset_after`.      |
| file_size_limit | Number | The maximum number of bytes that can be uploaded in the time frame denoted by `reset_after`. |

### Example

```json
{
  "reset_after": 10,
  "limit": 5,
  "file_size_limit": 50000000 // 50MB
}
```

## EffisRateLimits Object

Represents the rate limits for Effis. These rate limits denote how often files can
be requested from the CDN, as well as maximum file size limits.

| Field       | Type               | Description                                                 |
| ----------- | ------------------ | ----------------------------------------------------------- |
| assets      | EffisRateLimitConf | The rate limit information for the handling of Assets.      |
| attachments | EffisRateLimitConf | The rate limit information for the handling of Attachments. |

## Headers

Every request to a rate limited route returns some rate limit related headers, you're
supposed to use these to properly rate limit any clients or API wrapper you make.

| Header                    | Type   | Description                                                                         |
| ------------------------- | ------ | ----------------------------------------------------------------------------------- |
| X-RateLimit-Reset         | Number | The reset interval length of a bucket in milliseconds.                              |
| X-RateLimit-Max           | Number | The maximum number of requests that can be sent per bucket interval.                |
| x-RateLimit-Last-reset    | Number | The UNIX timestamp of the last time this bucket interval was reset in milliseconds. |
| x-RateLimit-Request-Count | Number | The amount of requests done by the client for this bucket.                          |
| <hr />                    | <hr /> | <hr />                                                                              |
| X-RateLimit-Byte-Max      | Number | The maximum number of bytes that can be sent per bucket interval                    |
| X-RateLimit-Sent-Bytes    | Number | The number of sent bytes by the client for this bucket interval.                    |

> **Notes**
>
> These headers also exist on `429` responses.
>
> <hr />
>
> The UNIX timestamps here all use the actual UNIX epoch and not the Eludris one.

### How To Implement Rate Limiting

Ideally how rate limiting is implemented is that you check the response headers
on every request and check if you've ran out of requests for this interval.

If so, you prevent any other requests on the same bucket for `Now - (X-RateLimit-Last-Reset + X-RateLimit-Reset)`
milliseconds.

Additionally - when dealing with Effis - you should also check if the uploaded files
abide by the limits of file sizes in the [InstanceInfo](./instance_info.md) payload.

You should also keep track of how many more bytes you can send and limit requests
according to that.

## Relevant Endpoints

| Method | Endpoint                                          |
|--------|---------------------------------------------------|
| GET    | [`Oprish /rate_limits`](../oprish/rate_limits.md) |
| GET    | [`Oprish /`](../oprish/instance_info.md)          |
