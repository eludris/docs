# Downloading an Effis file

## Download file from bucket

<span class="request-method"><b>GET</b></span> `/<bucket>/<id>/download`

Download the file with the provided id from the provided bucket.

### Returns

The file with the provided id from the provided bucket. This is returned with header
`Content-Disposition: attachment` set.

## Download attachment

<span class="request-method"><b>GET</b></span> `/<id>/download`

This route acts as a shorthand for <span class="request-method"><b>GET</b></span> `/attachments/<id>/download`,
the same logic applies.
