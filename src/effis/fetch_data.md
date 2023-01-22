# Fetching file data from Effis

## Fetch file data from bucket

<span class=requestmethod><b>GET</b></span> `/<bucket>/<id>/data`

Fetch the file data of the file with the provided id from the provided bucket.

### Returns

The [FileData](../models/files.md#filedata-object) object of the file with the
provided id from the provided bucket.

## Fetch attachment file data

<span class=requestmethod><b>GET</b></span> `/<id>/data`

This route acts as a shorthand for <span class=requestmethod><b>GET</b></span> `/attachments/<id>/data`,
the same logic applies.

## Example

```sh
curl \
  https://effis.tooty.xyz/370617076959762069670199317/data
```

```json
{
  "id": "370617076959762069670199317",
  "name": "kaas",
  "bucket": "attachments",
  "spoiler": true,
  "metadata": {
    "type": "image",
    "width": 128,
    "height": 128
  }
}
```
