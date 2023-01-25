# Dealing with static Effis files

## Fetch static file

<span class="request-method"><b>GET</b></span> `/static/<name>`

Fetch the static file with the provided name. Static files are added by the instance
owner and cannot be externally modified.

## Returns

The static file with the provided name. This is returned with header `Content-Disposition:
inline` set.

## Download static file

<span class="request-method"><b>GET</b></span> `/static/<name>/download`

Download the static file with the provided name.

## Returns

The static file with the provided name. This is returned with header `Content-Disposition:
attachment` set.
