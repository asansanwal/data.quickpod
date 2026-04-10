# Console Operations FAQ

This FAQ explains what each major user-facing console operation is for, when to use it, and when to choose a different workflow. It is grounded in the current QuickPod console behavior across Search, Pods, Templates, Storage, Clusters, Serverless, Secrets, and Settings.

## Scope

This page focuses on user-facing console operations, not internal admin tools or host-only listing controls.

Related docs:

* [Introduction](introduction.md)
* [Search & Launch](search-and-launch.md)
* [Pods](pods.md)
* [Templates](templates.md)
* [Storage & Cloud Sync](storage-and-cloud-sync.md)
* [Clusters](clusters.md)
* [Serverless](serverless.md)
* [Secrets](secrets.md)
* [Settings](settings.md)

## Search and launch

### Which search page should I use?

Use [GPU Search](https://console.quickpod.io/) when your workload needs one or more GPUs. Use [CPU Search](https://console.quickpod.io/cpu-pod-search) when the workload is CPU-only or you want lower-cost general compute.

### What does creating a pod let me configure?

The current create flow lets you evaluate and set:

* the offer you are renting
* the template you will launch
* a pod name
* disk size
* an optional coupon
* an optional persistent volume
* optional secret bindings

This means pod creation is not only a hardware choice. It is the point where compute, image, storage, and secret mounting are combined into one launch request.

### When should I change filters instead of launching the first matching offer?

Change filters first when cost, location, duration limits, VRAM, or reliability matter more than getting any immediate capacity. The search console is meant to narrow to a suitable offer before you commit to a launch.

### Should I pick a template before clicking Create Pod?

Yes. In QuickPod, the template is part of the launch design, not an afterthought. It determines image path, startup behavior, launch mode, published ports, and readme guidance. If you are not sure which template to use, review [Templates](templates.md) first.

### How should I evaluate launch-time storage choices?

Use pod disk size when the data only needs to live with that pod.

Use a volume when the data should survive beyond one pod lifecycle, be reused by later launches, or participate in cloud sync workflows.

### Search and launch quick reference

| Operation | Use it when | Avoid it when | Notes |
| --- | --- | --- | --- |
| Search GPU offers | You need GPU-backed compute | The workload is CPU-only | Filters, price, region, duration, and reliability matter before launch |
| Search CPU offers | You need CPU-only compute or lower-cost runtime | You need CUDA or GPU VRAM | CPU templates and CPU offers are separate from GPU launch flows |
| Create Pod | You are ready to rent a specific offer | You are still comparing hardware, templates, or storage strategy | The launch modal is where template, disk, volume, secrets, and coupon are combined |
| Attach volume at launch | You need persistent data that outlives one pod | The workload is disposable | Volumes are better than leaving stopped pods around only to preserve disk data |
| Attach secrets at launch | The container needs credentials or token files | The value is safe to keep in plain text, which is uncommon | Secrets are mounted read-only and can optionally populate a *_FILE environment variable |

## Pods

### What is the Pods page for after launch?

The [Pods](pods.md) page is the operational control center after creation. It is where you monitor readiness, connect, inspect logs, rename the workload, and run lifecycle actions such as start, stop, restart, and destroy.

### What is the practical difference between stop and destroy?

Stop pauses the workload but keeps the pod and its storage footprint. Destroy removes the pod entirely.

Use stop when you expect to resume the workload later and want to keep the pod around.

Use destroy when the workload is finished and you no longer need the pod or its attached pod-local storage.

### Why does stop not eliminate all cost?

Because stopped pods can still retain storage. The console distinguishes active running spend from stopped-storage spend specifically so you can see that keeping a stopped pod is not free.

### When should I use start?

Use start when a previously stopped pod should resume. Start is a recovery or continuation action, not a substitute for launch. If you need different hardware, different ports, or a different base template, create a new pod instead.

### When should I use restart?

Use restart when the running container needs a clean process restart but you do not want to destroy and recreate the whole pod. Restart is appropriate for application-level recovery, not for changing the pod's core launch configuration.

### What are logs and connect for?

Use logs to inspect recent runtime output and troubleshoot container startup or application issues.

Use connect when the pod is ready and you need interactive access or the console-provided connection details.

### Can I rename a pod?

Yes. Renaming is useful for organization and does not change the underlying rented hardware or template definition.

### Pod operations quick reference

| Operation | Use it when | Avoid it when | Notes |
| --- | --- | --- | --- |
| Connect | The pod is ready and you need interactive access | The pod is still provisioning or connection details are not ready | Connection depends on the pod exposing the right route or access mode |
| View logs | You need startup or runtime output | You need to change template settings, not inspect runtime behavior | Logs are usually the first place to check a failed startup |
| Rename | You want clearer organization in the Pods list | You expect it to change the workload internals | Rename is cosmetic and organizational |
| Stop | You want to pause compute and possibly resume later | You want to eliminate the pod completely | Storage cost can remain after stop |
| Start | You want to resume a stopped pod | You need a new hardware choice or a different base config | Start resumes the existing pod rather than creating a new one |
| Restart | You want to recycle the running container cleanly | You need to change launch-time inputs like template, disk, or offer | Restart is best for runtime recovery |
| Destroy | You are finished with the pod | You still need the pod or its pod-local disk state | Destroy is the terminal cleanup action |

## Templates

### What is the difference between select, create, edit, and clone?

Select marks a template as the one you want to use in launch flows.

Create makes a brand-new template in your account.

Edit changes one of your existing templates.

Clone copies another template into your account so you can customize it without editing the original source template.

### When should I clone instead of create from scratch?

Clone when a public or community template is already close to what you need. This is usually the fastest way to keep known-good ports, commands, and image defaults while making only your required changes.

Create from scratch when the workload, image, or launch behavior is materially different from existing templates.

### What should I edit in a template versus at pod launch?

Edit the template when the setting is part of the reusable workload definition, such as:

* image path
* Docker options and published ports
* launch mode
* entrypoint behavior
* on-start script
* recommended disk size
* template readme

Change values at pod launch when the setting is pod-specific, such as the chosen offer, final pod name, coupon, attached volume, or selected secrets.

### When should I use a private registry template?

Use private registry settings when the image is not publicly pullable. Put registry credentials in the template's dedicated private registry fields instead of embedding them in commands or documentation text.

### What does sharing with the community mean?

Community sharing makes your template discoverable to other users for cloning and reuse. Use it for general-purpose or reusable workloads, not for account-specific or secret-dependent templates.

### Should I delete a template?

Delete a template when it is obsolete, duplicated, or no longer safe to present as a launch option. Do not delete a template solely because one pod created from it is no longer needed. Pods and templates are separate lifecycle objects.

### Template operations quick reference

| Operation | Use it when | Avoid it when | Notes |
| --- | --- | --- | --- |
| Select | You want this template to be the default choice for launch flows | You only want to inspect it | Select improves launch speed but does not modify the template |
| Create template | You need a reusable workload definition | A public or community template already matches closely | Best for repeated launches and consistent settings |
| Edit template | You own the template and need to change reusable behavior | You need a one-off pod-specific override | Edit changes the reusable definition for future launches |
| Clone template | You want to reuse an existing public or community template safely | You need to modify the original publisher's template directly | Clone creates your own copy |
| Share with community | The template is general, reusable, and safe to publish | The template depends on private assumptions or account-specific setup | Community sharing improves discoverability |
| Delete template | The template is obsolete or duplicated | The only issue is a single bad pod launch | Delete removes it from your template library |

## Storage and cloud sync

### When should I create a volume?

Create a volume when data needs to outlive one pod or be reused by future pods, clusters, or sync jobs. Volumes are the correct persistence layer for reusable data.

### When is cloud sync better than manually copying files?

Cloud sync is better when you need repeatable transfers between QuickPod storage and a provider such as Amazon S3, Backblaze B2, Dropbox, or Google Drive. It is especially useful for scheduled imports, exports, backups, and ongoing data refresh.

### What is the difference between manual-only and recurring schedule?

Manual-only means the sync target exists but runs only when you start a job.

Recurring schedule means QuickPod will run sync jobs automatically using the configured cadence and timezone.

### Should I save cloud credentials as reusable secrets?

Yes. Reusable secret-backed credentials are better than repeatedly pasting provider credentials into setup flows. That keeps the sync configuration cleaner and reduces credential sprawl.

### Storage operations quick reference

| Operation | Use it when | Avoid it when | Notes |
| --- | --- | --- | --- |
| Create volume | You need persistent storage independent of one pod | The workload is disposable and temporary | Volumes are reusable across later workflows |
| Delete volume | The data is no longer needed | The volume is still attached to an active workflow | Treat deletion as data lifecycle cleanup |
| Create cloud sync target | You need repeatable movement between a volume and a cloud provider | You only need a one-time local copy | Targets store provider, direction, remote path, and schedule behavior |
| Run manual sync | You want an on-demand transfer | You need unattended recurring movement | Manual runs are safer while validating a new target |
| Enable recurring schedule | You need automated sync cadence | The data movement should stay operator-controlled | Timezone and cadence matter for predictable job timing |
| Edit cloud sync target | Provider settings or schedule rules changed | The existing target is correct and only needs a one-off run | Edit is better than recreating when the relationship stays the same |

## Clusters

### When should I create a cluster instead of a single pod?

Create a cluster when you want multiple replicas, service routing, rolling redeploy behavior, or autoscaling and schedule controls. Use a single pod when you only need one isolated runtime and do not need cluster-level service management.

### What do the main cluster actions mean?

Create cluster starts a multi-replica deployment based on a chosen template and offer strategy.

Start and stop control the cluster-managed replicas as a group.

Scale changes desired replica count.

Rolling redeploy replaces replicas gradually while respecting readiness gates.

Delete cluster removes the cluster and its managed replicas.

### What should I use rolling redeploy for?

Use rolling redeploy when the workload definition or release state has changed and you want the cluster to refresh replicas safely instead of dropping everything at once.

### What are services for on a cluster?

Cluster services define how traffic reaches ready replicas. They also carry protocol, context path, and health-check behavior that higher-level features such as Serverless can build on.

### How should I think about autoscaling, scheduled scaling, and placement?

Use autoscaling for load-responsive replica changes.

Use scheduled scaling for predictable business-hour or batch windows.

Use placement rules when topology, isolation, geography, or machine-type preferences matter. Tighter placement improves control but can reduce compatible capacity.

### What do cluster storage modes affect?

Storage mode controls whether replicas have no cluster volume, a shared volume, or shard-specific volumes. This choice changes how data is shared, isolated, and scaled across replicas.

### Cluster operations quick reference

| Operation | Use it when | Avoid it when | Notes |
| --- | --- | --- | --- |
| Create cluster | You need a managed multi-replica workload | One pod is sufficient | Clusters add service, rollout, scaling, and policy surfaces |
| Start cluster | The cluster is stopped and should resume | You actually need more replicas or a new template revision | Start resumes the current cluster state |
| Stop cluster | You need to pause the whole deployment | You only need to remove one replica or service definition | Stop affects all cluster-managed replicas |
| Scale cluster | You need more or fewer replicas | The main need is a new release rollout | Scale changes capacity, not workload definition |
| Rolling redeploy | You need to refresh replicas safely | The cluster is only paused and should simply be started | Readiness-gated rollout reduces abrupt downtime |
| Add or edit service | You need a stable service endpoint or health-aware routing | You only need direct pod access | Services are the routing layer for clusters and serverless |
| Edit policy | You need to change autoscaling, schedules, rollout, or placement behavior | Nothing about control policy has changed | Placement strictness can reduce available capacity |
| Delete cluster | The deployment is permanently no longer needed | You only want to pause or redeploy | Delete destroys the cluster-managed workload |

## Serverless

### What has to exist before I create a serverless endpoint?

You need a cluster and at least one cluster service first. Serverless publishes that cluster service behind a managed invoke path.

### What is the difference between hot service and warm service?

The hot service is the main active backend for requests. The warm service is an optional secondary service used in the current serverless model where the endpoint needs both primary and standby-style routing behavior.

### When should I edit an endpoint versus recreate it?

Edit when the endpoint still represents the same product surface and you only need to adjust slug, auth mode, timeout, active state, pricing, or service binding.

Recreate only when the endpoint concept itself should be replaced or removed.

### What does active versus inactive do?

Active keeps the endpoint available for normal invoke traffic. Inactive keeps the definition but disables normal use until you reactivate it.

### When should I inspect serverless logs?

Inspect logs when debugging requests, checking status codes, verifying routing behavior, or confirming that endpoint settings are producing the intended API behavior.

### Serverless operations quick reference

| Operation | Use it when | Avoid it when | Notes |
| --- | --- | --- | --- |
| Create endpoint | You want to expose a cluster service through a managed invoke URL | No cluster service exists yet | Serverless depends on cluster service definitions |
| Edit endpoint | Slug, auth, timeout, pricing, or service mapping needs adjustment | The endpoint should be retired entirely | Edit preserves the endpoint identity while changing configuration |
| Toggle active state | You want to temporarily disable or re-enable traffic | The endpoint should be deleted permanently | Inactive keeps configuration without serving normally |
| Review invoke URL and curl example | You need integration-ready request details | You are not ready to expose the service yet | The console generates practical invocation examples |
| Review logs | You need request and response visibility | You need runtime container logs instead | Endpoint logs are request-centric rather than container-centric |
| Delete endpoint | The API surface is no longer needed | A temporary pause is enough | Delete is irreversible cleanup |

## Secrets

### Why should I create a secret instead of storing the value in a template?

Because templates are reusable workload definitions and should not contain plaintext credentials. Secrets keep sensitive values out of template text, commands, and screenshots.

### How are secrets exposed inside the workload?

Secrets are mounted read-only under `/run/secrets`. If you set an environment-variable file mapping during attachment, QuickPod can also export a `*_FILE` style variable pointing to that mounted path.

### When should I revoke a secret?

Revoke when the credential is no longer trusted, no longer needed, or has been rotated elsewhere.

Do not revoke casually if active workflows still depend on it. Future pod creates or resets that reference the revoked secret can fail.

### Secret operations quick reference

| Operation | Use it when | Avoid it when | Notes |
| --- | --- | --- | --- |
| Create secret | A workload or sync target needs sensitive data | The value can safely live in plain text, which is rare | Plaintext is shown once and then cleared from the visible UI |
| Attach secret to pod | The container needs file-backed credentials or tokens | The workload has no secret requirement | Secret bindings are safer than embedding values in commands |
| Revoke secret | The value is obsolete, rotated, or compromised | Existing workflows still rely on it and have not been updated | Revoke blocks future reuse |

## Settings, billing, security, and notifications

### Where do account-level operations live?

Account profile, billing, invoices, security controls, reusable secrets, SSH public keys, notifications, and secure API keys are centered in [Settings](settings.md) and related authenticated routes.

### When should I create a secure API key?

Create one when an external script, CI job, or integration needs authenticated API access without using your browser session directly.

### What matters most about secure API keys?

The plaintext secret is shown once. Copy it immediately and store it securely. If it is lost or exposed, revoke it and create a new key rather than expecting the console to reveal the old secret again.

### When should I revoke an API key?

Revoke a key when the integration is retired, the scope is no longer appropriate, or you suspect exposure.

### Why should I use notifications instead of checking every page manually?

Notifications are the cross-product alert surface for pods, storage, hosting signals, billing, and system events. They reduce the need to poll each page for changes.

### Settings and security quick reference

| Operation | Use it when | Avoid it when | Notes |
| --- | --- | --- | --- |
| Add credit or manage billing | You need to fund or review account usage | You only need workload runtime diagnostics | Billing is separate from operational troubleshooting |
| Configure 2FA | You want stronger account protection | You are looking for API integration credentials | 2FA protects sign-in, not API automation |
| Add SSH public key | You plan to use SSH-based access patterns | The workload does not require SSH | Key management belongs in Settings, not templates |
| Create secure API key | Automation needs authenticated API access | A browser session is sufficient and no automation exists | Secrets are shown once only |
| Revoke secure API key | The key is stale or exposed | The integration still depends on it and has not been updated | Revocation is the safe rotation path |
| Review notifications | You need cross-product activity visibility | You need detailed runtime logs for one workload | Notifications summarize events; they do not replace full logs |

## Recommended workflow patterns

### I want to launch quickly but keep things clean later

1. Pick the right search page.
2. Select or clone a suitable template first.
3. Create the pod with the right disk, volume, and secrets.
4. Use Pods for runtime actions.
5. Destroy finished workloads instead of accumulating stopped pods.

### I want repeatable production-style behavior

1. Create or clone a stable template.
2. Move credentials into Secrets.
3. Use volumes for persistent data.
4. Move multi-replica services into Clusters.
5. Publish stable invoke paths through Serverless when external callers need an API surface.

### I want to reduce avoidable mistakes

1. Do not put credentials into template text or startup commands.
2. Do not use stop when you really mean destroy.
3. Do not use restart when the issue is actually a bad template or wrong ports.
4. Do not use a single pod when you actually need service routing and controlled rollout.
5. Do not revoke secrets or API keys before dependent workloads are updated.
