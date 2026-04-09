# CLI

QuickPod now has a Go-based CLI that covers the current user-facing QuickPod platform surface.

Repository:

* [https://github.com/quickpod/quickpod-cli](https://github.com/quickpod/quickpod-cli)

## What the current CLI covers

The current CLI supports workflows for:

* search
* pods
* templates
* clusters
* serverless endpoints
* storage volumes
* machines
* account and auth
* catalog data
* host stores
* security and 2FA

## Install

Latest installer:

```bash
curl -fsSL https://raw.githubusercontent.com/quickpod/quickpod-cli/main/install.sh | sh
```

## Build from source

```bash
git clone https://github.com/quickpod/quickpod-cli.git
cd quickpod-cli
go build -o quickpod
```

## Authentication

The CLI supports bearer-token and secure-API-key based use.

Examples:

```bash
quickpod auth login --email you@example.com
quickpod auth me
quickpod --api-key "$QUICKPOD_API_KEY" pods list --kind gpu
```

## Common commands

Search offers:

```bash
quickpod search gpu --type A100 --max-hourly 2.5
quickpod search cpu --max-hourly 0.25 --min-count 8
```

Work with pods:

```bash
quickpod pods list --kind gpu
quickpod pods get --kind gpu --pod POD_UUID
quickpod pods create --kind gpu --template TEMPLATE_UUID --offer OFFER_ID --disk 50 --name trainer
quickpod pods stop --kind gpu --pod POD_UUID
```

Work with templates:

```bash
quickpod templates list --scope public --kind gpu
quickpod templates list --scope community --kind cpu
```

Work with clusters and serverless:

```bash
quickpod clusters list
quickpod serverless list
```

## Related docs

* [API Documentation](api-documentation.md)
* [Serverless](../console/serverless.md)
* [Clusters](../console/clusters.md)

