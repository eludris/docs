# InstanceInfo object

Represents info about your instance.

| Field           | Type    | Description                                 |
|-----------------|---------|---------------------------------------------|
| instance_name   | String  | The name of the connected Eludris instance. |
| description     | String? | The description of the connected Eludris instance. If provided, this must be within 1 and 2048 characters long. |
| version         | String  | The version of the conencted Eludris instance. |
| message_limit   | Number  | The maximum allowed message content length. |
| oprish_url      | String  | The url to this instance's REST api.        |
| pandemonium_url | String  | The url to this instance's gateway.         |
| effis_url       | String  | The url to this instance's CDN.             |
| file_size       | Number  | The maximum number of bytes for an asset.   |
| attachment_file_size | Number  | The maximum number of bytes for an attachment. |

## Example

```json
{
  "instance_name": "WooChat",
  "description": "The most Woo place to Woo", // This field *can* be `null`, but it will always exist
  "message_limit": 2048,
  "oprish_url": "https://eludris.tooty.xyz/",
  "pandemonium_url": "wss://eludris.tooty.xyz/ws/",
  "effis_url": "https://effis.tooty.xyz/",
  "file_size": 20000000,
  "attachment_file_size": 25000000
}
```

## Relevant Endpoints

| Method | Endpoint                                 |
|--------|------------------------------------------|
| GET    | [`Oprish /`](../oprish/instance_info.md) |
