# InstanceInfo object

Represents info about your instance.

| Field         | Type    | Description                                 |
|---------------|---------|---------------------------------------------|
| instance_name | String  | The name of the connected Eludris instance. |
| description   | String? | The description of the connected Eludris instance. If provided, this must be within 1 and 2048 characters long. |
| message_limit | Number  | The maximum allowed message content length. |

## Example

```json
{
  "instance_name": "WooChat",
  "description": "The most Woo place to Woo", /* This field *can* be `null`, but it will always exist */
  "message_limit": 2048,
}
```

## Relevant Endpoints

| Method | Endpoint                          |
|--------|-----------------------------------|
| GET    | [`/`](../oprish/instance_info.md) |
