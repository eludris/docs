# Message object

Represents a message sent to or received from Eludris.
The message contains its author and content.

| Field   | Type   | Description                |
|---------|--------|----------------------------|
| author  | String | The author of the message. |
| content | String | The content of the message. At least one character; the upper bound is set per-instance inside `Eludris.toml`. This upper bound can be requested as part of the instance's InstanceInfo. |


# Relevant Endpoints

| Method | Endpoint
|--------|----------------------------------------------------|
| POST   | [`/messages/`](../routes/messages/create.md)       |
| GET    | [`/`](../routes/instance_info.md)
