# Billing

QuickPod uses prepaid account credit. You add credit first, then active workloads consume that balance over time.

## Current payment behavior

QuickPod's current console billing flow supports card checkout through Stripe and crypto-oriented billing flows exposed through the billing experience in Settings.

The billing area in the console also exposes invoice history and payment-link or payment-method related controls.

## How charges work

QuickPod separates compute cost from storage cost.

* Running pods accrue active compute cost plus storage cost.
* Stopped pods stop compute cost but continue to accrue storage cost while they still exist.
* Destroyed pods stop both compute and storage cost for that pod.
* Persistent storage and sync workflows can have their own associated costs depending on how you size or use them.

Bandwidth is not positioned as a separate line-item charge in the basic pod billing flow.

## What happens when your balance reaches zero

QuickPod does not immediately destroy your workloads and data when your balance reaches zero.

Instead, pods are stopped automatically so you can still recover data or add more credit. Storage charges may continue while the stopped pod still exists.

## Billing guidance

* Destroy pods you no longer need.
* Use volumes or cloud sync if you need persistence without leaving expensive pod disks running indefinitely.
* Review invoices and balance inside the authenticated settings experience regularly.

## Related console routes

* Authenticated billing area: `/settings`
* Public sign in: [https://console.quickpod.io/log-in](https://console.quickpod.io/log-in)
* Public sign up: [https://console.quickpod.io/sign-up](https://console.quickpod.io/sign-up)
