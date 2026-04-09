# Quick Start

QuickPod can be used directly from the public console at [console.quickpod.io](https://console.quickpod.io/).

Useful direct links:

* [GPU Search](https://console.quickpod.io/)
* [CPU Search](https://console.quickpod.io/cpu-pod-search)
* [Templates](https://console.quickpod.io/templates)
* [GPU Catalog](https://console.quickpod.io/gpu-types)
* [Host Stores](https://console.quickpod.io/host-stores)
* [Sign Up](https://console.quickpod.io/sign-up)
* [Log In](https://console.quickpod.io/log-in)

## 1. Create an account and add credit

Create an account first, then add prepaid credit from the console. QuickPod currently supports card checkout through Stripe and crypto checkout through the billing flow inside the console.

If your balance reaches zero or below, QuickPod stops your pods automatically. Stopped pods can still accrue storage charges until you destroy them.

## 2. Prepare your access method

QuickPod supports browser-based connection workflows and SSH-based access.

For browser access, many templates expose a web UI, notebook UI, or terminal-ready endpoint directly.

For SSH access, add your SSH public key in the authenticated console settings area before you create pods. If your workload needs a full SSH server, use a template that exposes SSH or clone a template and publish the right container port through the template's Docker options.

## 3. Choose a public or community template

Open [Templates](https://console.quickpod.io/templates) to browse public templates and community templates, or create your own template after login.

Templates define the image, launch mode, startup behavior, published ports, entrypoint behavior, and related readme content used during pod creation.

## 4. Search for an offer

Use [GPU Search](https://console.quickpod.io/) or [CPU Search](https://console.quickpod.io/cpu-pod-search) to filter current offers by hardware count, GPU or CPU type, location, cost, duration, VRAM, occupied state, and other hardware traits.

The search pages are public and can be used before login.

## 5. Set storage, secrets, and launch options

During pod creation, choose the storage allocation carefully because storage cost continues while a pod exists.

If your workload needs reusable credentials or mounted secrets, configure them from the authenticated console before launch and attach them to the pod during creation.

If you need persistent shared data across launches, review the storage features described in [Storage & Cloud Sync](console/storage-and-cloud-sync.md).

## 6. Create the pod

Creating the pod reserves the selected offer and starts the workload from the chosen template. The pod then appears on the Pods page in the authenticated console.

QuickPod shows startup and readiness state while the image is pulled, created, and initialized.

## 7. Connect and work

Once the pod becomes ready, connect through the pod's exposed public routes, browser tools, or SSH depending on how the template was configured.

Many public templates expose ports such as notebooks, dashboards, model APIs, or app UIs directly from the pod.

## 8. Stop or destroy when finished

Stopping a pod prevents active compute charges, but storage still accrues while the pod exists.

Destroy the pod when you no longer need the instance or its disk allocation. If you need persistence across sessions, move data into a volume or cloud-sync workflow first.
