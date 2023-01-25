# Version 0.3.1 Changes

This version mainly tries to address some developer-side frustrations with Eludris,
namely issues with having to make a branches in at least 2 repositories, make 2 pull
requests, merge the pull requests, update lockfiles, making a meta-repository branch
update the meta-repository's submodules, making a pull request then merging that
for _every single change_, also issues with syncing up versions.

Additionally Docker deployments have been greatly enhanced thanks to buildx powered
caching and much more (thanks @ooliver1).

## API Changes

### Oprish

The [`InstanceInfo`](./models/instance_info.md) payload now has an extra `version`
field to make it easier to make clients and API wrappers that will not break.

## Hosting Changes

Everything has been merged into one meta-repository using a [cargo workspace](https://doc.rust-lang.org/cargo/reference/workspaces.html)

Dockerfiles have also been greatly improved to use caching and other optimisations,
kudos to [@ooliver1](https://github.com/ooliver1) (and `docker buildx`) which helped
make this possible!

[PR](https://github.com/Eludris/eludris/pull/21)
