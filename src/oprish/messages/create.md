# Create Message

<span class=requestmethod><b>POST</b></span> `/messages`

Post a message to your Eludris instance.

## Parameters

The [Message](../../models/message.md) object to be posted to the Eludris instance.

> **Note**
>
> Message authors must be between 2-32 characters long.
>
> Message content must be at least 1 character long. The upper changes for every
> instance and hence should be fefched using the [instance info `/`](../instance_info.md)
> route.

## Returns

The [Message](../../models/message.md) object that was just sent.

## Example

```sh
curl \
  --json '{"author":"Not a weeb","content":"Hello, World!"}' \
  https://eludris.tooty.xyz/messages
```
```json
{
  "author": "Not a weeb",
  "content": "Hello, World!"
}
```
