# gestalt

a `gestalt` is something that is made of many parts and yet is somehow more than or different from the combination of its parts - a perfect name for an installation / setup script!

This repo is setup currently to support Ubuntu 22+ as the primary operating system, and additional operating systems may be added in the future.

## Secrets

The `.env.age` file in this repository is encrypted using [age](https://github.com/FiloSottile/age); you can setup `task` as outlined below and run `task install:age` or simply run `apt install age` on the server, or decrypt the file locally vs. moving to the server. In either case, you'll need to run `age -d .env.age` and enter the passphrase which will print out the secret values required for the scripts / installation. The areas today which require secrets are:

- `environment` shell script
- `BUILDKITE_AGENT_TOKEN` variable in `task install:buildkite`

## Taskfile

A pre-requisite to running any of the installation steps requires setup of [Taskfile](https://taskfile.dev/installation/), which should be as easy as running the below script:

```
sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d
```
(by default, this installs on the ``./bin`` directory relative to the working directory)

Once Taskfile is setup, you'll also need to get the contents of this repository onto the server via clone, or curl.