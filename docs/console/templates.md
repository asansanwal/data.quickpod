# Templates

Templates define how QuickPod launches a workload.

Direct link: [https://console.quickpod.io/templates](https://console.quickpod.io/templates)

## Template sources

The current Templates page includes:

* Public templates maintained for common QuickPod workflows
* Community templates shared by users
* Your own templates after login

## What a template contains

A template can define:

* image path
* template name and description
* launch mode
* Docker options, including published ports
* Docker run options and entry behavior
* CLI command or startup behavior
* disk recommendation
* readme content shown in the console
* template type used for GPU or CPU launch flows

## Common workflows

### Browse a public template

Use the public Templates page to inspect a template before login.

### Clone a public or community template

After login, clone a template into your account if you want to modify ports, startup commands, environment variables, or related launch settings.

### Create your own template

Authenticated users can create a brand-new template for internal use or publishing to the community.

### Share with the community

Templates can be marked for community sharing so other users can discover and clone them.

## Template types and launch pages

GPU templates are used from [GPU Search](https://console.quickpod.io/) and CPU templates are used from [CPU Search](https://console.quickpod.io/cpu-pod-search).

## Notes on ports

If your workload needs a web UI or API, publish the container port in the template's Docker options. Public template docs should make expected ports clear so users know what endpoint they are creating.
