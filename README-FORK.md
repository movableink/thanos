## movableink/thanos

This is a fork of `thanos`. It has the following changes.

* Adds a `receive.prefer-same-zone` flag to the `receive` command. This will update receive-router to send traffic to the same availability zone if there are enough pods in the that zone to support the replication factor. If there are not enough pods, then it will fallback to using the standard algorithm. The hashring json should have a `prefer_same_zone: true` for each endpoint. The `movableink/thanos-receive-controller` for automatically generates the json file as a kubernetes configmap.
* There are also a `Makefile-Movable` which has a couple of minor adjustments to running the build on github action runners.

Currently these changes are merged into the branch `movableink:release/v0-40-1`, which is branch from the v0.40.1 tag.
