# The Eludris CLI

The Eludris CLI is a tool that's meant to handle all the heavy lifting that comes
with initially starting an Eludris instance and managing it until the end of time.

> **Note**
>
> There are no plans to support Windows in the near future.

## Installation

TBA

## Usage

If you need any help with using the Eludris CLI at any time you should always check
the help command by running `eludris --help`. This will almost always tell you what
you want to know.

## Commands

Here's a list of the commands the Eludris CLI has along with a few extra notes.

### Deploy

```sh
sudo eludris deploy
```

This command will start up your Eludris instance using our pre-built Docker images.

Additionally if no instance is already found on your machine it will take you on
a step by step process to create one at `/usr/eludris`.

> **Note**
>
> When prompted to choose an editor ***do not*** chose VSCode or any of it's forks
> as this command is ran as root which will really mess up your root parition.
>
> Although you can still pass in a full command to use it you have been warned.

### Stop

```sh
sudo eludris stop
```

This command will stop all the microservices in your instance along with all the
other databases and such.

### Logs

```sh
sudo eludris logs
```

This command will show you your instance's logs and wait for new ones.

### Static

This is a command group which is meant to help deal with static assets.

#### Add

```sh
sudo eludris static add <path-to-file>
```

This command will add a new static asset to your instance's Effis.

#### Remove

```sh
sudo eludris static remove <name>
```

This command will remove a static asset from your instance's Effis.

### Attachments

This is a command group which is meant to help deal with Effis files in the attachments
bucket.

#### Remove

```sh
sudo eludris attachments remove <id>
```

This command will remove an attachment's file from your instance along with it's
database entry to prevent `500` errors.

### Clean

```sh
sudo eludris clean
````

This command will remove your Eludris instance along with all the database files.

> **Note**
>
> This will not clean up the docker images, you can remove those using `docker image rm <image names>*`
