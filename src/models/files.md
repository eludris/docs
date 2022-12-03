# FileMetadata object

Holds file type-dependent information of a file stored on Effis. This can be one of four variants:


## Text

Text metadata does not contain any special parameters.

| Field  | Type   | Description                                            |
|--------|--------|--------------------------------------------------------|
| type   | String | The type of file as a lowercase string, always "text". |


## Image

Image metadata contains the width and height of the image.

| Field  | Type   | Description                                             |
|--------|--------|---------------------------------------------------------|
| type   | String | The type of file as a lowercase string, always "image". |
| width  | Number | The width of the image in pixels.                       |
| height | Number | The height of the image in pixels.                      |


## Video

Video metadata contains the width and height of the video.

| Field  | Type   | Description                                             |
|--------|--------|---------------------------------------------------------|
| type   | String | The type of file as a lowercase string, always "video". |
| width  | Number | The width of the video in pixels.                       |
| height | Number | The height of the video in pixels.                      |


## Other

Metadata for other files only include the file type.

| Field  | Type   | Description                             |
|--------|--------|-----------------------------------------|
| type   | String | The type of file as a lowercase string. |


## Examples

```json
{
    "type": "text"
}

{
    "type": "image",
    "width": 5120,
    "height": 1440
}

{
    "type": "video",
    "width": 1920,
    "height": 1080
}

{
    "type": "other"
}
```


# FileData object

Represents a file stored on Effis.

| Field    | Type    | Description                                                         |
|----------|---------|---------------------------------------------------------------------|
| id       | Number  | The id of the file.                                                 |
| name     | String  | The name of the file.                                               |
| bucket   | String  | The bucket to which the file belongs.                               |
| spoiler? | Boolean | Whether this file is spoiler tagged. This is not provided if false. |
| metadata | Object  | A `FileMetadata` object containing meta-information about the file. |


## Example

```json
{
    "id": 12345678,
    "name": "kaas",
    "bucket": "attachments",
    "spoiler": true,
    "metadata": {
        "type": "image",
        "width": 7680,
        "height": 4320,
    }
}

{
    "id": 12345678,
    "name": "japanese goblin",
    "bucket": "attachments",
    "metadata": {
        "type": "other"
    }
}
```

## Relevant Endpoints

| Method | Endpoint
|--------|----------------------------------------------------|
| POST   | [`Effis /`](../effis/upload_files.md)               |
| POST   | [`Effis /<bucket>`](../effis/upload_files.md)       |
