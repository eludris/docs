# Instance Info

<span class=requestmethod><b>GET</b></span> `/`

Get information about the instance you're sending this request to.

Most of this data comes from the instance's configuration.

## Returns

The [InstanceInfo](../models/instance_info.md) object for the connected Eludris instance.

## Example

```sh
curl \
  https://eludris.tooty.xyz
```
```json
{
  "instance_name": "eludris",
  "description": "The *almost* official Eludris instance - ooliver.\nThis is **not** a testing instance as it is bridged to Eludis. Use your own local instance for testing.",
  "version": "0.3.1",
  "message_limit": 2048,
  "oprish_url": "https://api.eludris.gay",
  "pandemonium_url": "wss://ws.eludris.gay/",
  "effis_url": "https://cdn.eludris.gay",
  "file_size": 20000000,
  "attachment_file_size": 25000000
}
```
