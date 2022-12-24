# Hosting your own instance

One of our goals ever since the start is to make hosting Eludris instances as simple
and as friction free as possible. To that extent Eludris has provided an [`Eludris.toml`](./conf.md)
where you can configure your instance as much as you wish and also official docker
support to help you get started scoff free.

## Deploying an instance with Docker

We really recommend using [Docker](https://www.docker.com/) for production instances,
it helps keep all the microservices and the external tools they rely on all in one
neat group of containers without conflicting with anything else related to the host
system, and without you having to go around OS-dependant installing C libraries.

Deploying a production-ready Eludris instance with docker is only 3 simple steps:

1. Clone the [meta repository](https://github.com/eludris/eludris).

  This step requires you to have [Git](https://git-scm.com/) installed.
  After you have that. simply run the following command:

  ```sh
  git clone https://github.com/eludris/eludris && cd eludris
  ```

  What this does is it clones the meta repository then changes your shell's current
  directory to the newly cloned Eludris one.

2. Configure your instance.

  Now you just need to rename `.env.example` to `.env` and `ExampleEludris.toml`
  to `Eludris.toml` then open them in your favourite editor, besides the comments
  present in the files there is also a [page here](./conf.md) about instance configuration.

3. Start your instance.

  This step needs you to have - as you could've guessed - [Docker](https://www.docker.com/),
  additionally it requires you to have [docker-compose](https://docs.docker.com/compose/)
  to run all the microservices and their dependencies from one place without much
  effort.

  All you need to do is run this command:

  ```sh
  docker-compose up
  ```

  Docker should now start building all the microservices in release mode and after
  a short while (depending on your hardware, this may take a bit) you will have a
  functioning Eludris instance on your machine.

  You can find [Oprish](./oprish/index.md) at `0.0.0.0:7159`, [Pandemonium](./pandemonium/index.md)
  at `0.0.0.0:7160` and [Effis](./effis/index.md) at `0.0.0.0:7161`.

## Deploying on Bare Metal / Running a Development Instance

Now this is just a little bit more complicated, here's a quick rundown of what you
have to do:

1. Get the required dependencies
  You will need [KeyDB](https://docs.keydb.dev/docs/download) and [MariaDB](https://mariadb.com/downloads/),
  the latest version of both should work.

2. Get the latest version of `eludris/eludris`.

  ```sh
  git clone https://github.com/eludris/eludris && cd eludris
  ```

  You may also want update the submodules to use the `next` branch if you're trying
  to run a development instance or test a new feature, for that run this instead:

  ```sh
  git clone https://github.com/eludris/eludris --branch=next && cd eludris
  ```

3. Configure the `Eludris.toml` file & `.env`.

  `.env` is mostly optional thanks to somewhat sane defaults but you'll need to
  have an `eludris` database for MariaDB and a root user with the password as root,
  you can also just change the database URI from the `DATABASE_URL` environment variable.

  Additionally, I'd recommend throwing a `RUST_LOG="debug"` in there for debugging
  & logging purposes.

  For more info check out the [configuration page](./conf.md) of the docs.

4. Start the dependencies.

5. Start the microservices.

  Now what I'd recommend doing here first is building all the microservices at once,
  to do that, just run this command:

  ```sh
  cargo build --release
  ```

  After which you can just run these commands to start the microservices.

  ```sh
  cargo run --bin oprish --release
  cargo run --bin pandemonium --release
  cargo run --bin effis --release
  ```

  If you want faster build time for the price of slightly worse performance when
  you're for example testing, you can run the microservices in debug mode like so:

  ```sh
  cargo build
  ```

  ```sh
  cargo run --bin oprish
  cargo run --bin pandemonium
  cargo run --bin effis
  ```

  You will need to run each of these commands in it's own terminal buffer for.

  Depending on your hardware and whether you're building in release mode, this may
  take a bit :D

Congratulations, now you're self-hosting a development instance of Eludris on bare
metal!

If you did everything like in this documentation, you should have [Oprish](./oprish/index.md)
at `127.0.0.1:7159`, [Pandemonium](./pandemonium/index.md) at `127.0.0.1:7160` and
[Effis](./effis/index.md) at `127.0.0.1:7161`.
