# Message object

Represents a message sent to or received from Eludris.
The message contains its author and content.

| Field   | Type   | Description                |
|---------|--------|----------------------------|
| author  | String | The author of the message, between 2-32 characters long. |
| content | String | The content of the message. At least one character; the upper bound is set per-instance inside `Eludris.toml`. This upper bound can be requested as part of the instance's InstanceInfo. |

## Example

```json
{
  "author": "Frynus Mctronalds",
  "content": "dragon"
}
```

## Relevant Endpoints

| Method | Endpoint
|--------|----------------------------------------------------|
| GET    | [`Oprish /`](../oprish/instance_info.md)
| POST   | [`Oprish /messages/`](../oprish/messages/create.md)       |
