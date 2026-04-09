# Settings

The authenticated Settings area is now the control center for account configuration, billing, security, invoices, secure API keys, and secrets.

## What lives in Settings

### Account profile

Manage basic account profile fields, billing details, avatar, and payout-related information that belongs to your user account.

### Billing and invoices

Add credit, review invoice history, and manage linked payment methods. Billing behavior is covered in more detail in [Billing](billing.md).

### Security and two-factor authentication

QuickPod supports stronger account protection through email and authenticator-based two-factor flows inside the settings surface.

### Secure API keys

QuickPod supports secure API keys for automation and integrations. These are intended for scripted workflows rather than sharing your main session credentials.

### SSH public key

Add your SSH public key before creating pods if you want SSH-based access for workloads that expose or run SSH.

### Reusable secrets

Manage reusable secret values that can later be attached to pods or storage workflows without hardcoding values into templates.

### Notifications

Review notification history and configure category preferences for platform events such as pods, storage, hosting, billing, and system alerts.

## Related routes

These routes require authentication, but they are part of the current console experience that older docs often miss:

* `/settings`
* `/notifications`
* `/secrets`

Direct public login links:

* [Log In](https://console.quickpod.io/log-in)
* [Sign Up](https://console.quickpod.io/sign-up)
