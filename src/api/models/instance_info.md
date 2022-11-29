# InstanceInfo object

Represents a message sent to or received from Eludris.
The message contains its author and content.

| Field         | Type    | Description                                 |
|---------------|---------|---------------------------------------------|
| instance_name | String  | The name of the connected Eludris instance. |
| description   | String? | The description of the connected Eludris instance. If provided, this must be within 1 and 2048 characters long. |
| 


# Relevant Endpoints

| Method | Endpoint                          |
|--------|-----------------------------------|
| GET    | [`/`](../routes/instance_info.md) |
