# RatelimitError

The error raised when the client is ratelimited.

| Field       | Type   | Description                |
|-------------|--------|----------------------------|
| retry_after | Number | The number of seconds the client should wait before making new requests. |


# FileSizeRatelimitedError

The error raised when the client surpasses the maximum amount of bytes and is ratelimited.

| Field       | Type   | Description                |
|-------------|--------|----------------------------|
| retry_after | Number | The number of seconds the client should wait before making new requests. |
| bytes_left  | Number | The number of bytes the client has available until the ratelimit resets.


# ValidationError

The error raised when the supplied request body is invalid.

| Field      | Type   | Description                                  |
|------------|--------|----------------------------------------------|
| field_name | String | The name of the field that raised the error. |
| error      | String | The error that occurred.                     |


# NotFoundError

The error raised when the requested resource could not be found.


# ServerError

The error raised when an internal server error occurs.

| Field      | Type   | Description                                  |
|------------|--------|----------------------------------------------|
| error      | String | The name of the field that raised the error. |
