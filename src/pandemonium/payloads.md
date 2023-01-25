# Gateway Events

## General Structure

Events sent to and received from the gateway should always be of a common format. A field `op` specifies the opcode of the event, and an optional field `d` contains that event's data.

| Field | Type   | Description                                                                     |
| ----- | ------ | ------------------------------------------------------------------------------- |
| op    | String | The opcode of the event. This is a unique identifier in `SCREAMING_SNAKE_CASE`. |
| d?    | Object | A JSON-serialized object containing further information pertaining the event.   |

Here're a couple example payloads

```json
/* A payload with no data */
{
  "op": "FOO"
}
/* A couple of payloads with data */
{
  "op": "FOO",
  "d": {
    "bar": "baz"
    }
}
{
  "op": "FOO",
  "d": [
    "bar",
    "baz"
    ]
}
```

## Ping

The gateway expects to receive a ping every 45 seconds. A ping is a simple payload consisting of only an opcode. In response to a ping, the gateway will send back a pong.

| Field | Type   | Description      |
| ----- | ------ | ---------------- |
| op    | String | Always `"PING"`. |

### Example

```json
{
  "op": "PING"
}
```

## Pong

The response to a connected client's ping payload.

| Field | Type   | Description      |
| ----- | ------ | ---------------- |
| op    | String | Always `"PONG"`. |

### Example

```json
{
  "op": "PONG"
}
```

## Message Create

An event that is dispatched to all connected clients when a message is received. This event contains the message that triggered the event.

| Field | Type                            | Description                                  |
| ----- | ------------------------------- | -------------------------------------------- |
| op    | String                          | Always `"MESSAGE_CREATE"`.                   |
| d     | [Message](../models/message.md) | The message object that triggered the event. |

### Example

```json
{
  "op": "MESSAGE_CREATE",
  "d": {
    "author": "A certain woo",
    "content": "Woo!"
  }
}
```
