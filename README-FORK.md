## movableink/thanos

This is a fork of `thanos`. It has the following changes.

* Adds a `receive.prefer-same-zone` flag to the `receive` command. This will update receive-router to send traffic to the same availability zone if there are enough pods in the that zone to support the replication factor. If there are not enough pods, then it will fallback to using the standard algorithm. The hashring json should have a `prefer_same_zone: true` for each endpoint. The `movableink/thanos-receive-controller` for automatically generates the json file as a kubernetes configmap.
* The Receive process uses `THANOS_RECEIVE_AVAILABILITY_ZONE` to prefer same-zone replicas where the local zone has enough nodes, and falls back to the standard hashring otherwise.

Currently these changes are merged into the branch `movableink:release/v0-42-5`, which is based on the upstream v0.42.5 tag.
