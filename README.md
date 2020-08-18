# containerd-repackaging

This is a repository to rebuild/publish CentOS 8/RHEL 8 (el8) RPM's for `containerd.io` as a stopgap until `docker-ce` officially supports and produces CentOS 8 packages.

## Tagging

This repository has continuous integration via Drone that is powered by tag. The automation will automatically `clone` the `rancher/containerd-packaging` repository and build using the `master` branch of the packaging repository and performs the equivalent of a `make REF=${PARSED_TAG} docker.io/library/centos:8`. There is tag parsing/version logic built into this repository, with example tags and results given below.

|Tag              |RPM Repository          |Containerd Version|RPM Version |
|:----------------|:-----------------------|:-----------------|:-----------|
|`v1.2.13.testing`|`rpm-testing.rancher.io`|`v1.2.13`         |`1.2.13-3.2`|
|`v1.2.13.latest` |`rpm.rancher.io`        |`v1.2.13`         |`1.2.13-3.2`|
|`v1.2.13.stable` |`rpm.rancher.io`        |`v1.2.13`         |`1.2.13-3.2`|
|`v1.2.12.testing`|`rpm-testing.rancher.io`|`v1.2.12`         |`1.2.12-3.1`|
|`v1.2.12.latest` |`rpm.rancher.io`        |`v1.2.12`         |`1.2.12-3.1`|

**Important Note:** The `docker/containerd-packaging` repository has its own RPM versioning logic that takes the `containerd version` and selects the latest corresponding RPM version that exists in the changelog.