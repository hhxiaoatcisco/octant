![Logo][octant-logo]

[![](https://mermaid.ink/img/pako:eNptkcFuwjAMhl8l8mnTCmpDC7TaZRpD2mEnbqjSZFqvRDQJS1MxYLz72mztGMwn-3P-X459hEznBAlkJVbVTGBhUKaKNfGghMSS3X8OBmxWZ5trOhfV-pouaWXwD07YnVCWYUGXeGGNUAUrSOVkzputpHpB2aQ3txcNiZY66MZ24x2_AetNV4SbR11q0zeqnZCdsCnfa8w2XX0692s_1vsN2tkrcaBnNSeyPc5QPaH9V-9W8DvQSuuSiep1J8q8h6ZWvRY8kGQkiry5hNOlYNckKYWkSXN6w7q0KaSqfYq11Yu9yiCxpiYP6m3ebOTndh3cooLkCB-Q8HgyjKI44KNJPPKDkIce7CEJYj7kke_7EedTfzwKTh4ctG4M_GEYu5iOQ5_H0Th2dkvXbN1PXysNp9c?type=png)](https://mermaid.live/edit#pako:eNptkcFuwjAMhl8l8mnTCmpDC7TaZRpD2mEnbqjSZFqvRDQJS1MxYLz72mztGMwn-3P-X459hEznBAlkJVbVTGBhUKaKNfGghMSS3X8OBmxWZ5trOhfV-pouaWXwD07YnVCWYUGXeGGNUAUrSOVkzputpHpB2aQ3txcNiZY66MZ24x2_AetNV4SbR11q0zeqnZCdsCnfa8w2XX0692s_1vsN2tkrcaBnNSeyPc5QPaH9V-9W8DvQSuuSiep1J8q8h6ZWvRY8kGQkiry5hNOlYNckKYWkSXN6w7q0KaSqfYq11Yu9yiCxpiYP6m3ebOTndh3cooLkCB-Q8HgyjKI44KNJPPKDkIce7CEJYj7kke_7EedTfzwKTh4ctG4M_GEYu5iOQ5_H0Th2dkvXbN1PXysNp9c)

[![Build Status](https://github.com/vmware-tanzu/octant/workflows/preflight-checks/badge.svg)](https://github.com/vmware-tanzu/octant/workflows/preflight-checks/badge.svg)
![GitHub release](https://img.shields.io/github/release/vmware-tanzu/octant.svg)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/4142/badge)](https://bestpractices.coreinfrastructure.org/projects/4142)

> A highly extensible platform for developers to better understand the complexity of Kubernetes clusters.

Octant is a tool for developers to understand how applications run on a Kubernetes cluster. It aims to be part of the developer's toolkit for gaining insight and approaching complexity found in Kubernetes. Octant offers a combination of introspective tooling, cluster navigation, and object management along with a plugin system to further extend its capabilities.

## Features

* **Resource Viewer**

    Graphically visualize relationships between objects in a Kubernetes cluster. The status of individual objects are represented by color to show workload performance.

* **Summary View**

    Consolidated status and configuration information in a single page aggregated from output typically found using multiple kubectl commands.

* **Port Forward**

    Forward a local port to a running pod with a single button for debugging applications and even port forward multiple pods across namespaces.

* **Log Stream**

    View log streams of pod and container activity for troubleshooting or monitoring without holding multiple terminals open.

* **Label Filter**

    Organize workloads with label filtering for inspecting clusters with a high volume of objects in a namespace.

* **Cluster Navigation**

   Easily change between namespaces or contexts across different clusters. Multiple kubeconfig files are also supported.

 * **Plugin System**

   Highly extensible plugin system for users to provide additional functionality through gRPC. Plugin authors can add components on top of existing views.

## Usage

![Octant demo](web/src/assets/octant-demo.gif)

## Installation

### Package (Linux only)

1. Download the `.deb` or `.rpm` from the [releases page](https://github.com/vmware-tanzu/octant/releases).

2. Install with either `dpkg -i` or `rpm -i` respectively.

###  Windows

#### Chocolatey

1. Install using chocolatey with the following one-liner:

   ```sh
   choco install octant --confirm
   ```

#### Scoop

1. Add the [extras](https://github.com/lukesampson/scoop-extras) bucket.

   ```sh
   scoop bucket add extras
   ```

2. Install using scoop.

   ```sh
   scoop install octant
   ```

### macOS

#### Homebrew

1. Install using Homebrew with the following one-liner:

   ```sh
   brew install octant
   ```

### Download a Pre-built Binary (Linux, macOS, Windows)

1. Open the [releases page](https://github.com/vmware-tanzu/octant/releases) from a browser and download the latest tarball or zip file.

2. Extract the tarball or zip where `X.Y` is the release version:

    ```sh
    $ tar -xzvf ~/Downloads/octant_0.X.Y_Linux-64bit.tar.gz
    octant_0.X.Y_Linux-64bit/README.md
    octant_0.X.Y_Linux-64bit/octant
    ```

3. Verify it runs:

    ```sh
    $ ./octant_0.X.Y_Linux-64bit/octant version
    ```

## Nightly Builds

Nightly builds of Octant are available for download.

Please note that nightly builds maybe less stable than our tagged releases and are intended to allow early access to
preview upcoming features and for plugin authors who want access to the latest plugin APIs.

[Browse nightly builds](https://console.cloud.google.com/storage/browser/octant-nightlies)

## Getting Started

Before starting Octant, make sure you have access to a healthy cluster. If kubectl is installed, test using `kubectl cluster-info`.

Start running Octant:

`$ octant`

Octant should immediately launch your default web browser on `127.0.0.1:7777`.

Octant uses the default web browser on the system to act as the UI client. In the future Octant will ship with a UI.

For setting extra configuration such as what kubeconfig or context to use at startup, refer to the [documentation](https://reference.octant.dev/).

## Supported Versions

Octant versions follow [Semantic Versioning](https://semver.org/) where a given version number represents `MAJOR.MINOR.PATCH`.

Patch releases address bug fixes, regressions, and small enhancements.

Minor releases contain security fixes, API changes, and significant enhancements such as UI changes or new components.

Major releases contain breaking changes that are not guaranteed to be backwards compatible. Octant versions before 1.0 should not be considered stable and API may change between minor releases.

### Supported Version Skew

Version of Octant are compiled against a version of client-go.

Octant follows an `n±1` policy for versions of Kubernetes similar to kubectl. For example, Octant `0.16.0` uses the Kubernetes 1.19 client. So version `0.16.0` can be used with Kubernetes 1.18, 1.19, and 1.20.

## Plugins

Plugins are a core part of Octant in the Kubernetes ecosystem. A plugin can read objects and allows users to add components to Octant's views.

An example plugin can be found in [`cmd/octant-sample-plugin`](cmd/octant-sample-plugin) and installed to the default plugin path with `go run build.go install-test-plugin`.

Some plugins can be found on GitHub in the [`#octant-plugin`](https://github.com/topics/octant-plugin) topic (tag).

Documentation for plugin components can be found in the [Plugins section](https://reference.octant.dev/?path=/docs/docs-plugins-1-getting-started--page) of the documentation.

## Discussion

Feature requests, bug reports, and enhancements are welcome. Contributors, maintainers, and users are encouraged to collaborate through these communication channels:

 - [Kubernetes Slack](http://slack.k8s.io/) in the [#octant](https://kubernetes.slack.com/app_redirect?channel=CM37M9FCG) channel
 - [Twitter](https://twitter.com/projectoctant)
 - [Google group](https://groups.google.com/forum/#!forum/project-octant/)
 - [GitHub issues](https://github.com/vmware-tanzu/octant/issues)

## Contributing

Contributors will need to sign a DCO (Developer Certificate of Origin) with all changes. We also ask that a changelog entry is included with your pull request. Details are described in our [contributing](CONTRIBUTING.md) documentation.

See our [hacking](HACKING.md) guide for getting your development environment setup.

See our [roadmap](ROADMAP.md) for tentative features in a 1.0 release.

## License

Octant is available under the [Apache License, Version 2.0](LICENSE)

[octant-logo]: /web/src/assets/octant-logo.png
