# OprishRatelimits Object

Represents the ratelimits for Oprish (REST-api). This denotes the ratelimits on each individual route.

| Field          | Type              | Description                |
|----------------|-------------------|----------------------------|
| info           | [RatelimitConf](./ratelimits.md) | The ratelimit information for the [/](../routes/instance_info.md) route. |
| message_create | [RatelimitConf](./ratelimits.md) | The ratelimit information for the [/messages](../routes/messages/create.md) route. |
| ratelimits     | [RatelimitConf](./ratelimits.md) | The ratelimit information for the [/ratelimits](../routes/ratelimits.md) route. |


# Relevant Endpoints

| Method | Endpoint                                 |
|--------|------------------------------------------|
| GET    | [`/ratelimits`](../routes/ratelimits.md) |
