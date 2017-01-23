# MkDocs in Docker with Bootswatch themes

This repo contains instructions on how to build a docker image that will run
[MkDocs](http://www.mkdocs.org/) to build your project docs, it also includes the MkDocs Bootswatch themes.

## Docker registry

This image is available on the [Docker registry](https://index.docker.io/) as
[jujhars13/mkdocs](https://index.docker.io/u/jujhars13/mkdocs/) it's been forked from Nate Jones' [nate/mkdocs](https://index.docker.io/u/nate/mkdocs/) hard work.
## Running

This docker container can be run in one of two ways.

### Using volumes:

The image will build whatever site is mounted in `/mkdocs`.

```
$ docker run --rm -v /host/path:/mkdocs jujhars13/mkdocs
```

### Without volumes:

When the `STREAM` environment variable is set, this image expects a tgz on stdin with the root of the mkdocs compatible source. The built site is output as a tarball to stdout:

```
$ tar -czf - . | docker run -i -e STREAM=1 --rm jujhars13/mkdocs > output.tgz
```

To replicate the 'with volumes' version without volumes, pipe to a tar command:

```
$ tar -czf - . | docker run -i -e STREAM=1 --rm jujhars13/mkdocs | tar -xzf -
```

# License

Copyright © 2014 Nate Jones, forked by Jujhar Singh in 2017

Distributed under the MIT license.
