# Fetching files from Effis

## Fetch file from bucket

<span class=requestmethod><b>GET</b></span> `/<bucket>/<id>`

Fetch the file with the provided id from the provided bucket.

### Returns

The file with the provided id from the provided bucket. This is returned with header
`Content-Disposition: inline` set.

## Fetch attachment

<span class=requestmethod><b>GET</b></span> `/<id>`

This route acts as a shorthand for <span class=requestmethod><b>GET</b></span> `/attachments/<id>`,
the same logic applies.
