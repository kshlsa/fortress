<!--
order: 1
-->

# Installation

Build and install the Fortress binaries from source or using Docker. {synopsis}

## Pre-requisites

- [Install Go 1.17.5+](https://golang.org/dl/) {prereq}
- [Install jq](https://stedolan.github.io/jq/download/) {prereq}

## Install Go

::: warning
Fortress is built using [Go](https://golang.org/dl/) version `1.17.5+`
:::

```bash
go version
```

:::tip
If the `torqued: command not found` error message is returned, confirm that your [`GOPATH`](https://golang.org/doc/gopath_code#GOPATH) is correctly configured by running the following command:

```bash
export PATH=$PATH:$(go env GOPATH)/bin
```

:::

## Install Binaries

::: tip
The latest {{ $themeConfig.project.name }} [version](https://github.com/hardiksa/fortress/releases) is `{{ $themeConfig.project.binary }} {{ $themeConfig.project.latest_version }}`
:::

### GitHub

Clone and build {{ $themeConfig.project.name }} using `git`:

```bash
git clone https://github.com/hardiksa/fortress.git
cd fortress
make install
```

Check that the `{{ $themeConfig.project.binary }}` binaries have been successfully installed:

```bash
torqued version
```

### Docker

You can build {{ $themeConfig.project.name }} using Docker by running:

```bash
make build-docker
```

The command above will create a docker container: `hardiksa/fortress:latest`. Now you can run `torqued` in the container.

```bash
docker run -it -p 26657:26657 -p 26656:26656 -v ~/.torqued/:/root/.torqued hardiksa/fortress:latest torqued version

# To initialize
# docker run -it -p 26657:26657 -p 26656:26656 -v ~/.torqued/:/root/.torqued hardiksa/fortress:latest torqued init test-chain --chain-id test_9000-2

# To run
# docker run -it -p 26657:26657 -p 26656:26656 -v ~/.torqued/:/root/.torqued hardiksa/fortress:latest torqued start
```

### Releases

You can also download a specific release available on the {{ $themeConfig.project.name }} [repository](https://github.com/hardiksa/fortress/releases) or via command line:

```bash
go install github.com/hardiksa/fortress@latest
```
