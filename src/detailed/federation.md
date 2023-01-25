# Federation

Eludris will be federated, meaning anyone can host their own instance and instances
can communicate with each other so that any user on one instance can interact with
others on any other instance.

## Federation Implementation

All routes where other instances can request or submit data will have an
additional `/external` path (like `/external/this/channels/:channel_id/`).

For info about how IDs are created read [this](./index.md#ids).

`/external` routes will follow specific rules, these being:

A new instance (one the home instance has never seen before) will have to first
send an `identify` payload.
This payload is simple as it just provides a shared secret token key that both instances
can use to identify each other (in case an instance's domain gets compromised or
changed) and the instance's id.

`/external` routes will take both Oprish payloads and Pandemonium payloads in the
form of HTTP requests.

For example, let's say an instance A has a community with a channel that has users
from other instances, one of which is B.
When a user from instance B sends a message to `B's domain/external/A's ID/channels/:channel_id/messages`,
B will send the Oprish message payload to `A's domain/external/this/channels/:channel_id/message`.

When a user from instance A sends a message the opposite will happen with A sending
a request to B's external route in form of a Pandemonium payload.
