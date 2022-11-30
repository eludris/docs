# Create Message

<span class=requestmethod><b>POST</b></span> `/messages/`

Post a message to the connected Eludris instance.

## Parameters

The [Message](../../models/message.md) object to be posted to the Eludris instance.


## Returns

The Message object that was just sent.


## Errors

| Code | Description                                                    |
|------|----------------------------------------------------------------|
| 422  | The provided Message payload was incorrect.                    |
| 429  | Ratelimited; too many requests were made in a given timeframe. |
