# Upload file to bucket

<span class=requestmethod><b>POST</b></span> `/<bucket>`

Upload a file to Effis under a specific bucket. At the moment, only the `attachments` bucket is supported.


## Parameters

A `multipart/form-data` body containing the file to be uploaded and whether or not it should be spoiler tagged.

| Field   | Type    | Description                                        |
|---------|---------|----------------------------------------------------|
| file    | File    | The file to be uploaded.                           |
| spoiler | Boolean | Whether or not this file should be spoiler tagged. |


## Returns

A [FileData](../models/files.md#filedata-object) object containing information about the file as processed by Effis. This includes helpful parameters such as the file's id, which can then be used to fetch the file from Effis.


## Errors

| Code | Description |
|------|-------------|
| 422  | 
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |




# Upload attachment

<span class=requestmethod><b>POST</b></span> `/`

A shorthand for making a POST request to the attachment bucket (`/attachments`); that is, for uploading files to the attachment bucket.


## Parameters

A `multipart/form-data` body containing the file to be uploaded and whether or not it should be spoiler tagged.

| Field   | Type    | Description                                        |
|---------|---------|----------------------------------------------------|
| file    | File    | The file to be uploaded.                           |
| spoiler | Boolean | Whether or not this file should be spoiler tagged. |


## Returns

A [FileData](../models/files.md#filedata-object) object containing information about the file as processed by Effis. This includes helpful parameters such as the file's id, which can then be used to fetch the file from Effis.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |




# Fetch file from bucket

<span class=requestmethod><b>GET</b></span> `/<bucket>/<id>`

Fetch the file with the provided id from the provided bucket.


## Returns

The file with the provided id from the provided bucket. This is returned with header `Content-Disposition: inline` set.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |




# Fetch file data from bucket

<span class=requestmethod><b>GET</b></span> `/<bucket>/<id>/data`

Fetch the file data of the file with the provided id from the provided bucket.


## Returns

The [FileData](../models/files.md#filedata-object) object of the file with the provided id from the provided bucket.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |




# Download file from bucket

<span class=requestmethod><b>GET</b></span> `/<bucket>/<id>/download`

Download the file with the provided id from the provided bucket.


## Returns

The file with the provided id from the provided bucket. This is returned with header `Content-Disposition: attachment` set.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |




# Fetch attachment

<span class=requestmethod><b>GET</b></span> `/<id>`

Fetch the file with the provided id from the attachments bucket. This is a shorthand for making a GET request to the attachments bucket (`/attachments/<id>`).


## Returns

The attachment with the provided id. This is returned with header `Content-Disposition: inline` set.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |




# Fetch attachment file data

<span class=requestmethod><b>GET</b></span> `/<id>/data`

Fetch the file data of the attachment with the provided id. This is a shorthand for making a GET request to the attachments bucket (`/attachments/id/data`).


## Returns

The [FileData](../models/files.md#filedata-object) object of the attachment with the provided id.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |




# Download attachment

<span class=requestmethod><b>GET</b></span> `/<id>/download`

Download the attachment with the provided id. This is a shorthand for making a GET request to the attachments bucket (`/attachments/id/download`).


## Returns

The attachment with the provided id. This is returned with header `Content-Disposition: attachment` set.


## Errors

| Code | Description |
|------|-------------|
| 429  | [Ratelimited](../models/errors.md#ratelimiterror); too many requests were made in a given timeframe, or the maximum filesize limit for this timeframe was exceeded. |
