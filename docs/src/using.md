# Using Quilkin

There are two choices for running Quilkin:

* Binary
* Container image

## Binary

The release binary can be downloaded from the 
[Github releases page](https://github.com/googleforgames/quilkin/releases).

## Container Image

For each [release](https://github.com/googleforgames/quilkin/releases), there is a container image built and
hosted on Google Cloud [Artifact Registry](https://cloud.google.com/artifact-registry).

The latest production release can be found under the tag: 

```
us-docker.pkg.dev/quilkin/release/quilkin:{{QUILKIN_VERSION}}
```

Which can be browsed as [us-docker.pkg.dev/quilkin/release/quilkin](https://us-docker.pkg.dev/quilkin/release/quilkin).

The [entrypoint](https://docs.docker.com/engine/reference/builder/#entrypoint) of the container is to run `/quilkin` 
with no arguments, therefore arguments will need to be supplied. See the [documentation below](#command-line-interface) 
for all command line options.

## Command-Line Interface

Quilkin provides a variety of different commands depending on your use-case.
The primary entrypoint of the process is `run`, which runs Quilkin as a reverse
UDP proxy.  To see a basic usage of the command-line interface run through the
[netcat with Quilkin quickstart](./quickstarts/netcat.md). 

For more advanced usage, checkout the [`quilkin::Cli`] documentation or run:

```shell
$ quilkin --help
{{#include ../../target/quilkin.commands}}
```

## File Based Configuration

For use cases that utilise functionality such as:
 
* A static set of Filters 
* Multiple static Endpoints
* Static metadata on Endpoints

Quilkin also provides a yaml based config file as well.
See the [File Configuration](./file-configuration.md) documentation for details.

## Logging
By default Quilkin will log `INFO` level events, you can change this by setting
the `RUST_LOG` environment variable. See [`log` documentation][log-docs] for
more advanced usage.

> If you are debugging Quilkin set the `RUST_LOG` environemnt variable to `quilkin=trace`, to filter trace level 
> logging to only Quilkin components. 

[log-docs]: https://docs.rs/env_logger/0.9.0/env_logger/#enabling-logging
[`quilkin::Cli`]: ../api/quilkin/struct.Cli.html
