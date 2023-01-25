# Version 0.3.2 Changes

This version addresses some issues related to deploying production-ready instances
of Eludris by providing pre-built docker images and a simple CLI.

## API changes

- All mentions of `ratelimit` have become `rate_limit`, this should not break anything.

## Hosting Changes

- Pre-built Docker images now exist, long are gone the days of sitting around for
  20 minutes waiting for oprish to build, and welcome to the age of deployments taking
  less than a minute.
- A CLI has been created which overhauls the process of creating and managing your
  own Eludris instance, for more info, read the new [CLI](./cli.md) docs!

[PR](https://github.com/Eludris/eludris/pull/31)
