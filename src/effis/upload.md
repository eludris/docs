# Uploading files to Effis

## Upload file to bucket

<span class=requestmethod><b>POST</b></span> `/<bucket>`

Upload a file to Effis under a specific bucket. At the moment, only the `attachments`
bucket is supported.

### Parameters

A `multipart/form-data` body containing the file to be uploaded and whether or not
it should be spoiler tagged.

| Field    | Type    | Description                                        | Default  |
|----------|---------|----------------------------------------------------|----------|
| file     | File    | The file to be uploaded.                           |          |
| spoiler? | Boolean | Whether or not this file should be spoiler tagged. | `false`  |

### Returns

A [FileData](../models/files.md#filedata-object) object containing information about
the file as processed by Effis. This includes helpful parameters such as the file's
id, which can then be used to fetch the file from Effis.

## Upload attachment

<span class=requestmethod><b>POST</b></span> `/`

This route acts as a shorthand for <span class=requestmethod><b>POST</b></span> `/atatchments/`,
the same logic applies.

## Example

```sh
curl \
  -F "file=@kaas.png" \
  -F "spoiler=true" \
  https://effis.tooty.xyz/
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
