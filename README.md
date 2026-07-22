<p align="center">
  <a href="https://postqueen.ai">
    <img src="https://postqueen.ai/icon.svg" width="76" alt="PostQueen" />
  </a>
</p>

<h1 align="center">PostQueen Helm Chart</h1>

<p align="center">
  <strong>Deploy PostQueen on Kubernetes.</strong><br />
  The official Helm chart for PostQueen — the open-source, AI-native social media scheduler.
</p>

<p align="center">
  <a href="https://postqueen.ai">Website</a> ·
  <a href="https://app.postqueen.ai">Live App</a> ·
  <a href="https://docs.postqueen.ai">Docs</a> ·
  <a href="https://github.com/GkhanKINAY/postqueen-app">App Repository</a> ·
  <a href="https://github.com/GkhanKINAY/postqueen-docker-compose">Docker Compose</a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-blue.svg" alt="License: Apache-2.0"></a>
  <img src="https://img.shields.io/badge/chart-1.1.0-6d28d9" alt="Chart version 1.1.0">
  <img src="https://img.shields.io/badge/app-3.0.4-7c3aed" alt="App version 3.0.4">
  <img src="https://img.shields.io/badge/Helm-3.0+-0f1689" alt="Helm 3.0+">
</p>

---

## About this chart

This Helm chart deploys the [PostQueen](https://postqueen.ai) application on a Kubernetes cluster. It ships the app together with optional bundled PostgreSQL and Redis subcharts, a ConfigMap for non-sensitive settings, and a Secret for credentials — so a full deployment can be configured entirely through `values.yaml`.

Prefer not to run Kubernetes? PostQueen also runs with plain [Docker Compose](https://github.com/GkhanKINAY/postqueen-docker-compose).

> This chart is a fork of the [Postiz Helm chart](https://github.com/gitroomhq/postiz-helmchart) (Apache-2.0). Thanks to its original maintainers for the foundation.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.0+
- PV provisioner support in the underlying infrastructure (if persistence is required)

## Installing the Chart

The chart is distributed as an OCI artifact from the GitHub Container Registry, so **no `helm repo add` is required**.

To install the chart with the release name `postqueen`:

```bash
helm install postqueen oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app
```

This deploys PostQueen with the default configuration — including bundled PostgreSQL and Redis. Before exposing it publicly you should at minimum set a unique `secrets.JWT_SECRET` and the connection strings described in [Configuration](#configuration). The [Parameters](#parameters) section lists everything that can be tuned.

> **Temporal is bundled.** PostQueen uses [Temporal](https://temporal.io) for scheduling and publishing. By default this chart deploys a Temporal server with its own PostgreSQL (persistence + visibility, no Elasticsearch) and wires the app to it automatically — nothing to configure. To use an existing/external Temporal instead, set `temporal.enabled=false` and `temporal.externalAddress` to its `host:port`.

To upgrade an existing release after changing values or pulling a newer chart:

```bash
helm upgrade postqueen -f custom-values.yaml oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app
```

> **Tip:** List all releases with `helm list`.

## Uninstalling the Chart

To uninstall/delete the `postqueen` release:

```bash
helm uninstall postqueen
```

This removes all the Kubernetes components associated with the chart and deletes the release. Persistent volumes provisioned by the bundled PostgreSQL/Redis are not deleted automatically — remove their PVCs manually if you no longer need the data.

## Configuration

Application settings are split into two maps in `values.yaml`:

- **`env`** — non-sensitive values, rendered into a **ConfigMap**.
- **`secrets`** — credentials and connection strings, rendered into a **Secret**.

Both are loaded into the app container via `envFrom`, so every key becomes an environment variable at runtime.

### Environment variables (`env`)

| Parameter | Description | Default |
| --- | --- | --- |
| `env.FRONTEND_URL` | Public URL of the frontend | `http://localhost:4200` |
| `env.NEXT_PUBLIC_BACKEND_URL` | Public URL of the backend API (baked into the frontend at runtime) | `http://localhost:3000` |
| `env.BACKEND_INTERNAL_URL` | In-cluster URL the frontend uses to reach the backend | `http://backend:3000` |
| `env.UPLOAD_DIRECTORY` | Local filesystem path for uploaded media | `""` |
| `env.NEXT_PUBLIC_UPLOAD_STATIC_DIRECTORY` | Public path used to serve uploaded media | `""` |
| `env.NX_ADD_PLUGINS` | Nx plugin flag (leave as-is for most deployments) | `"false"` |
| `env.IS_GENERAL` | Enable general (self-host) mode | `"true"` |
| `temporal.enabled` | Deploy a bundled Temporal server (+ its own PostgreSQL) and auto-wire the app to it | `true` |
| `temporal.externalAddress` | `host:port` of an external Temporal — used only when `temporal.enabled` is `false` | `""` |
| `temporal.image.tag` | Temporal `auto-setup` image tag | `"1.28.1"` |
| `temporal.postgresql.persistence.size` | PVC size for Temporal's PostgreSQL | `8Gi` |

### Secrets (`secrets`)

Every key below is stored in the chart's Secret. Leave a key empty to disable the corresponding feature; set only what you need.

| Parameter | Description | Default |
| --- | --- | --- |
| `secrets.DATABASE_URL` | PostgreSQL connection string used by the app | `""` |
| `secrets.REDIS_URL` | Redis connection string used by the app | `""` |
| `secrets.JWT_SECRET` | Secret used to sign auth tokens — **set a unique value** | `""` |
| `secrets.X_API_KEY` | X (Twitter) OAuth API key | `""` |
| `secrets.X_API_SECRET` | X (Twitter) OAuth API secret | `""` |
| `secrets.LINKEDIN_CLIENT_ID` | LinkedIn OAuth client ID | `""` |
| `secrets.LINKEDIN_CLIENT_SECRET` | LinkedIn OAuth client secret | `""` |
| `secrets.REDDIT_CLIENT_ID` | Reddit OAuth client ID | `""` |
| `secrets.REDDIT_CLIENT_SECRET` | Reddit OAuth client secret | `""` |
| `secrets.GITHUB_CLIENT_ID` | GitHub OAuth client ID | `""` |
| `secrets.GITHUB_CLIENT_SECRET` | GitHub OAuth client secret | `""` |
| `secrets.RESEND_API_KEY` | [Resend](https://resend.com) API key for transactional email | `""` |
| `secrets.CLOUDFLARE_ACCOUNT_ID` | Cloudflare account ID (R2 object storage) | `""` |
| `secrets.CLOUDFLARE_ACCESS_KEY` | Cloudflare R2 access key | `""` |
| `secrets.CLOUDFLARE_SECRET_ACCESS_KEY` | Cloudflare R2 secret access key | `""` |
| `secrets.CLOUDFLARE_BUCKETNAME` | Cloudflare R2 bucket name | `""` |
| `secrets.CLOUDFLARE_BUCKET_URL` | Public base URL of the R2 bucket | `""` |

> **The app always reads its database and cache endpoints from `secrets.DATABASE_URL` and `secrets.REDIS_URL`** — the chart does not auto-derive them from the bundled subcharts. With a release named `postqueen` and the default bundled services, they typically look like:
>
> ```yaml
> secrets:
>   DATABASE_URL: "postgresql://postqueen:postqueen-password@postqueen-postgresql:5432/postqueen"
>   REDIS_URL: "redis://:postqueen-redis-password@postqueen-redis-master:6379"
> ```

### Example: a real deployment

Create a `custom-values.yaml`:

```yaml
env:
  FRONTEND_URL: "https://social.example.com"
  NEXT_PUBLIC_BACKEND_URL: "https://social.example.com/api"

secrets:
  JWT_SECRET: "change-me-to-a-long-random-string"
  DATABASE_URL: "postgresql://postqueen:postqueen-password@postqueen-postgresql:5432/postqueen"
  REDIS_URL: "redis://:postqueen-redis-password@postqueen-redis-master:6379"

ingress:
  enabled: true
  className: nginx
  hosts:
    - host: social.example.com
      paths:
        - path: /
          pathType: Prefix
          port: 80
```

Then install (or upgrade) with:

```bash
helm install postqueen -f custom-values.yaml \
  oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app
```

You can also override individual keys inline with `--set`, for example:

```bash
helm install postqueen \
  --set secrets.JWT_SECRET=change-me \
  oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app
```

> **Tip:** Use the shipped [`values.yaml`](charts/postqueen/values.yaml) as a starting point for your own configuration.

## Parameters

The following table lists the configurable parameters of the chart and their defaults. Application settings (`env.*` and `secrets.*`) are documented separately under [Configuration](#configuration).

### Core

| Parameter | Description | Default |
| --- | --- | --- |
| `replicaCount` | Number of app replicas | `1` |
| `image.repository` | App image repository | `ghcr.io/gkhankinay/postqueen-app` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `image.tag` | Image tag (falls back to chart `appVersion` when empty) | `latest` |
| `imagePullSecrets` | Secrets for pulling from a private registry | `[]` |
| `serviceAccount.create` | Create a service account | `true` |
| `serviceAccount.name` | Service account name (generated when empty) | `""` |
| `service.type` | Kubernetes service type | `ClusterIP` |
| `service.port` | Service port (maps to container port `5000`) | `80` |
| `service.additionalPorts` | Extra service ports | `[]` |

### Ingress

| Parameter | Description | Default |
| --- | --- | --- |
| `ingress.enabled` | Create an Ingress resource | `false` |
| `ingress.className` | IngressClass to use | `""` |
| `ingress.annotations` | Ingress annotations | `{}` |
| `ingress.hosts` | List of hosts, each with a nested `paths` list (`path`, `pathType`, `port`) | `[{host: chart-example.local, paths: [{path: /, pathType: Prefix, port: 80}]}]` |
| `ingress.tls` | TLS configuration | `[]` |
| `ingress.extraRules` | Additional raw ingress rules | `[]` |

### Database & cache (bundled subcharts)

| Parameter | Description | Default |
| --- | --- | --- |
| `postgresql.enabled` | Deploy the bundled Bitnami PostgreSQL | `true` |
| `postgresql.auth.username` | Bundled PostgreSQL username | `postqueen` |
| `postgresql.auth.password` | Bundled PostgreSQL password | `postqueen-password` |
| `postgresql.auth.database` | Bundled PostgreSQL database name | `postqueen` |
| `redis.enabled` | Deploy the bundled Bitnami Redis | `true` |
| `redis.auth.password` | Bundled Redis password | `postqueen-redis-password` |

### Storage, scheduling & extras

| Parameter | Description | Default |
| --- | --- | --- |
| `extraVolumes` | Additional pod volumes. When left empty, an `emptyDir` named `uploads-volume` is mounted automatically | `[]` |
| `extraVolumeMounts` | Additional volume mounts. When left empty, `uploads-volume` is mounted at `/uploads` | `[]` |
| `extraContainers` | Sidecar containers | `[]` |
| `resources` | Container resource requests/limits | `{}` |
| `autoscaling.enabled` | Enable a HorizontalPodAutoscaler | `false` |
| `autoscaling.minReplicas` | Minimum replicas when autoscaling | `1` |
| `autoscaling.maxReplicas` | Maximum replicas when autoscaling | `100` |
| `autoscaling.targetCPUUtilizationPercentage` | Target CPU utilization | `80` |
| `nodeSelector` | Node selector for pod assignment | `{}` |
| `tolerations` | Pod tolerations | `[]` |
| `affinity` | Pod affinity rules | `{}` |

Specify parameters with the `--set key=value[,key=value]` argument, or with a values file via `-f custom-values.yaml` (see [Configuration](#configuration)).

## Configuration and installation details

### External database support

To connect PostQueen to a database outside the cluster (for example a managed service), set `postgresql.enabled: false` so the bundled PostgreSQL is not deployed, then point the app at your database with the **`secrets.DATABASE_URL`** connection string:

```yaml
postgresql:
  enabled: false

secrets:
  DATABASE_URL: "postgresql://user:password@db.example.com:5432/postqueen"
```

### External Redis support

Similarly, set `redis.enabled: false` and provide your Redis endpoint through **`secrets.REDIS_URL`**:

```yaml
redis:
  enabled: false

secrets:
  REDIS_URL: "redis://:password@redis.example.com:6379"
```

### Persistence

When the bundled subcharts are enabled, PostgreSQL and Redis each request a [Persistent Volume](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) via dynamic provisioning, so their data survives pod restarts. Uploaded media is stored on the app pod's `uploads-volume`, which defaults to an `emptyDir` (ephemeral). For durable uploads, either configure object storage with the `secrets.CLOUDFLARE_*` keys, or supply a persistent `extraVolumes`/`extraVolumeMounts` pair pointing at `/uploads`.

## Upgrading

### To 1.1.0

The chart is published at `oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app`, and the default database/Redis credentials were renamed to `postqueen*`. If you installed a `1.0.x` release, install the new chart under the `postqueen` release name (or set `--set postgresql.auth.*` / `redis.auth.*` to keep your existing credentials).

### To 1.0.0

This was the first major release of the Helm chart.

## Contributing

Issues and pull requests for this chart are welcome — please open them in the [postqueen-app repository](https://github.com/GkhanKINAY/postqueen-app/issues), where all PostQueen development is tracked.

## License

This chart is licensed under the Apache License 2.0 — see the [LICENSE](LICENSE) file for details. It is a fork of the [Postiz Helm chart](https://github.com/gitroomhq/postiz-helmchart) (Apache-2.0) — thanks to its original maintainers.
