# Errors

All error messages in Eludris come in one format as follows:

| Field   | Type   | Description |
|---------|--------|-------------|
| status  | Number | The status code of the error. |
| message | String | A message which explains the error. |
| data?   | Object | The error's associated data. |

### Example

```json
/* An error without data */
{
  "status": 404,
  "message": "The requested resource cannot be found"
}
/* An error with data */
{
  "status": 429,
  "message": "You have been ratelimited",
  "data": {
      "retry_after": 42069,
    }
}
```

## RatelimitedError

The error raised when the client is ratelimited.

| Field       | Type   | Description |
|-------------|--------|-------------|
| retry_after | Number | The number of milliseconds the client should wait before making new requests. |

### Example

```json
{
  "status": 429,
  "message": "You have been ratelimited",
  "data": {
      "retry_after": 42069,
    }
}
```

## FileSizeRatelimitedError

The error raised when the client surpasses the maximum amount of bytes and is ratelimited.

| Field       | Type   | Description |
|-------------|--------|-------------|
| retry_after | Number | The number of milliseconds the client should wait before making new requests. |
| bytes_left  | Number | The number of bytes the client has available until the ratelimit resets.

### Example

```json
{
    "status": 429,
    "message": "You have surpassed your file size limit",
    "data": {
        "retry_after": 42069,
        "bytes_left": 1337
      }
}
```

## ValidationError

The error raised when the supplied request body is invalid.

| Field      | Type   | Description |
|------------|--------|-------------|
| field_name | String | The name of the field that raised the error. |
| error      | String | The error that occurred. |

### Example

```json
{
  "status": 422,
  "message": "Invalid request body",
  "data": {
      "field_name": "content",
      "error": "I disagree with your opinion"
    }
}
```

## NotFoundError

The error raised when the requested resource could not be found.

This error has no special data.

### Example

```json
{
  "status": 404,
  "message": "The requested resource cannot be found"
}
```

## ServerError

The error raised when an internal server error occurs.

| Field      | Type   | Description |
|------------|--------|-------------|
| error      | String | The name of the field that raised the error. |

### Example

```json
{
  "status": 500,
  "message": "The server encountered an error while performing the requested action",
  "data": {
      "error": "Shine didn't confirm ;-;"
    }
}
```
