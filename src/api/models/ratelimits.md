# RatelimitConf

Represents a ratelimit for a specific part of the Eludris spec.

| Field       | Type   | Description |
|-------------|--------|-------------|
| reset_after | Number | The number of seconds the client should wait before making new requests.
| limit       | Number | The number of requests that can be made within the timeframe denoted by `reset_after`. |


# InstanceRatelimits

Represents all ratelimits that apply to the connected Eludris instance. This includes individual ratelimit information for Oprish (REST-api), Pandemonium (Gateway), and Effis (CDN).

| Field       | Type   | Description |
|-------------|--------|-------------|
| oprish      | [OprishRatelimits](./oprish_ratelimits.md) | The ratelimits that apply to the connected Eludris instance's REST api. |
| pandemonium | RateLimitConf | The ratelimits that apply to the connected Eludris instance's gateway. |
| effis       | [EffisRatelimits](./effis_ratelimits.md) | The ratelimits that apply to the connected Eludris instance's CDN. |


# Relevant Endpoints

| Method | Endpoint                                 |
|--------|------------------------------------------|
| GET    | [`/ratelimits`](../routes/ratelimits.md) |