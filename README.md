# TOST ONOS Development Build Environment

Docker build environment capable of producing a version of **ONOS** and needed apps that can run with **TOST**. Typically the **ONOS** restful api would be used to include apps after **ONOS** is started.

## Build

We provide multiple targets for the Makefile

`onos` is used to setup the workspace for the build. It is possible to build the image using a specific branch (export `ONOS_BRANCH` variable) or a specific review (export `ONOS_REVIEW` variable). It clones `onos` if does not exist in the workspace and uses current workspace unless above vars are defined.

`onos-build` is used to build a specialized **Docker** image of **ONOS** that will contain only the apps needed by **TOST**. It depends on `onos-checkout` target

```sh
# Build a Docker image from the current workspace.
make onos-build
```

```sh
# Build a Docker image from the onos-2.2 branch.
export ONOS_BRANCH=onos-2.2 && make onos-build
```

```sh
# Build a Docker image from the review 123456.
export ONOS_REVIEW=12345 && make onos-build
```

## Clean

Use target `clean` to remove the local artificats generated by the tool.

```sh
make clean
```

## Push

We provide multiple push-target for the Makefile. You need to first login by `docker login` command to push the image on a repository.

`onos-push` will push the produced `ONOS_IMAGENAME` on the defined `DOCKER_REGISTRY` and `DOCKER_REPOSITORY`.

```sh
export DOCKER_REPOSITORY=onosproject/ make onos-push
```
