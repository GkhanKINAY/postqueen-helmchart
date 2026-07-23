<p align="center">
  <a href="https://postqueen.ai">
    <img src=".github/assets/header.svg" width="840" alt="PostQueen: the queen of your posts, your AI social media assistant" />
  </a>
</p>

<h3 align="center">🆕&nbsp; NEW: run your social media just by talking to your AI. Plan a month of content, generate it and schedule it to 30+ networks, then review it all on a visual calendar.</h3>

<br/>

<p align="center">
  <strong>Stop writing posts by hand.</strong> Tell PostQueen what is happening, a sale, a new product, a milestone, and she finds the best hook, picks a photo in your brand colors, writes a version for every platform, and lines it up on your calendar. A social media manager that never sleeps, for a creator or a whole company.
</p>

<p align="center">
  <strong>PostQueen</strong> is an open-source alternative to <strong>Buffer, Hootsuite, Sprout Social, Later</strong> and more.
</p>

<br/>

<p align="center">
  <a href="https://postqueen.ai">Website</a> &nbsp;·&nbsp;
  <a href="https://postqueen.ai/pricing">Pricing</a> &nbsp;·&nbsp;
  <a href="https://docs.postqueen.ai">Docs</a> &nbsp;·&nbsp;
  <a href="https://api.postqueen.ai/docs">API Reference</a> &nbsp;·&nbsp;
  <a href="https://postqueen.ai/agent">Agents</a> &nbsp;·&nbsp;
  <a href="https://postqueen.ai/mcp">MCP</a> &nbsp;·&nbsp;
  <a href="https://www.npmjs.com/package/postqueen">CLI</a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-blue.svg" alt="License: Apache-2.0"></a>
  <img src="https://img.shields.io/badge/chart-1.1.0-6d28d9" alt="Chart version 1.1.0">
  <img src="https://img.shields.io/badge/app-3.0.4-7c3aed" alt="App version 3.0.4">
  <img src="https://img.shields.io/badge/Helm-3.0+-0f1689" alt="Helm 3.0+">
</p>

<p align="center">
  <img src=".github/assets/channels.svg" width="780" alt="Publishes to 30+ social networks" />
</p>

<p align="center">
  <a href="https://postqueen.ai"><img src=".github/assets/cta-cloud.svg" height="48" alt="Start free for 7 days" /></a>
  &nbsp;&nbsp;
  <a href="https://github.com/GkhanKINAY/postqueen-docker-compose"><img src=".github/assets/cta-selfhost.svg" height="48" alt="Self-host it free" /></a>
</p>

---

## 👑 Everything PostQueen does for you

<p align="center">
  <img src=".github/assets/features.svg" width="880" alt="Scheduling, AI Assistant, AI Design, AI Video, Auto Actions, Teamwork, Analytics, Cross-posting" />
</p>

All of it is real, and all of it is yours to run: PostQueen is fully open-source, so you can use the managed cloud or host the whole thing yourself.

---

## 💬 Just talk to your AI

Think of PostQueen as the social media manager on your team, one you simply talk to. Tell her what is happening and she does the thinking: she finds a hook that fits your topic, picks an image with colors that match your brand, writes a version for each platform, and drops it on your calendar. Ask her in plain words, in **your own language** (PostQueen speaks 16 languages, Turkish included), by text or, if your assistant supports voice, hands-free by speaking.

Just say what you want:

> *"Plan a month of content for our coffee shop and fill the calendar."*

> *"Take this photo of today's special and put it on Instagram at lunchtime."*

> *"We just hit 10k followers, write a warm thank-you post for all our channels."*

> *"Turn my latest YouTube video into posts for X, LinkedIn and Threads."*

**You stay in control.** Everything lands in your calendar first, so you can read it, tweak it, or delete it before it goes out. Prefer to sign off on every single post? Ask her to save them as drafts, and nothing publishes until you schedule it yourself.

<br/>

<p align="center">
  <img src=".github/assets/works-with.svg" width="820" alt="Works with Claude Code, OpenClaw, Hermes, ChatGPT, Codex, Cursor, Gemini CLI, Aider, Cline and Warp" />
</p>

Already using an AI assistant? Point it at PostQueen and it runs everything over the same Agent CLI and hosted MCP server, so you drive your social media from the tool you are already in.

### In your terminal

Install PostQueen as a skill, then Claude Code, Codex, Cursor or Gemini CLI can post for you:

```bash
# Install the skill
npx skills add GkhanKINAY/postqueen-agent

# Set your API key
export POSTQUEEN_API_KEY=your_api_key

# List your connected platforms
postqueen integrations:list

# Create your first post
postqueen posts:create \
  -c "Hello from PostQueen!" \
  -s "2026-01-01T12:00:00Z" \
  -i "your-integration-id"
```

Set-up guides: [Claude Code »](https://postqueen.ai/claude-code) &nbsp;·&nbsp; [Codex »](https://postqueen.ai/codex) &nbsp;·&nbsp; [Cursor »](https://postqueen.ai/cursor)

### From any chat app

Message OpenClaw from WhatsApp, Telegram, Slack or Discord. It runs quietly on your machine, picks up your message, finds your connected accounts, uploads the media and schedules the posts, all while you get on with your day:

```text
You: Post my blog article to X, LinkedIn and Reddit with the cover image,
     schedule it for tomorrow at 9am.

OpenClaw: Done! Posts scheduled:
  • X          tomorrow, 9:00 AM
  • LinkedIn   tomorrow, 9:00 AM
  • Reddit     tomorrow, 9:00 AM  (r/programming)
```

Set-up guides: [OpenClaw »](https://postqueen.ai/openclaw) &nbsp;·&nbsp; [Hermes »](https://postqueen.ai/hermes-agent) &nbsp;·&nbsp; [ChatGPT »](https://postqueen.ai/chatgpt)

**Any other agent works too.** Everything is a CLI command or an MCP call, so you can point any MCP client at PostQueen: **Gemini CLI, Aider, Cline, Warp, Windsurf**, or your own scripts. Start from the [Agent CLI](https://postqueen.ai/agent) or [MCP](https://postqueen.ai/mcp) guide.

---

## Deploy on Kubernetes

This Helm chart deploys the [PostQueen](https://postqueen.ai) application on a Kubernetes cluster. It ships the app together with optional bundled PostgreSQL and Redis subcharts, a ConfigMap for non-sensitive settings, and a Secret for credentials, so a full deployment can be configured entirely through `values.yaml`.

The chart is published under its chart name `postqueen-app` (set in [`Chart.yaml`](charts/postqueen/Chart.yaml)), which is why the OCI reference ends in `.../charts/postqueen-app`. In this repository the chart source lives in the `charts/postqueen/` directory, so install commands use the chart name `postqueen-app` while any local edit points at `charts/postqueen/values.yaml`.

Prefer not to run Kubernetes? PostQueen also runs with plain [Docker Compose](https://github.com/GkhanKINAY/postqueen-docker-compose).

### Prerequisites

- Kubernetes 1.19+
- Helm 3.0+
- PV provisioner support in the underlying infrastructure (if persistence is required)

### Installing the chart

The chart is distributed as an OCI artifact from the GitHub Container Registry, so **no `helm repo add` is required**.

To install the chart with the release name `postqueen`:

```bash
helm install postqueen oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app
```

This deploys PostQueen with the default configuration, including bundled PostgreSQL and Redis. Before exposing it publicly you should at minimum set a unique `secrets.JWT_SECRET` and the connection strings described in [Configuration](#configuration). The [Parameters](#parameters) section lists everything that can be tuned.

> **Requires a Temporal server.** PostQueen uses [Temporal](https://temporal.io) for scheduling and publishing: the app reads `TEMPORAL_ADDRESS` (default `localhost:7233`). This chart does **not** bundle Temporal, so run one alongside the release (or point at an existing cluster) and set `env.TEMPORAL_ADDRESS` to its `host:port`. Without it the UI loads but scheduled publishing will not run.

To upgrade an existing release after changing values or pulling a newer chart:

```bash
helm upgrade postqueen -f custom-values.yaml oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app
```

> **Tip:** List all releases with `helm list`.

### Uninstalling the chart

To uninstall/delete the `postqueen` release:

```bash
helm uninstall postqueen
```

This removes all the Kubernetes components associated with the chart and deletes the release. Persistent volumes provisioned by the bundled PostgreSQL/Redis are not deleted automatically, so remove their PVCs manually if you no longer need the data.

### Configuration

Application settings are split into two maps in `values.yaml`:

- **`env`**: non-sensitive values, rendered into a **ConfigMap**.
- **`secrets`**: credentials and connection strings, rendered into a **Secret**.

Both are loaded into the app container via `envFrom`, so every key becomes an environment variable at runtime.

#### Environment variables (`env`)

| Parameter | Description | Default |
| --- | --- | --- |
| `env.FRONTEND_URL` | Public URL of the frontend | `http://localhost:4200` |
| `env.NEXT_PUBLIC_BACKEND_URL` | Public URL of the backend API (baked into the frontend at runtime) | `http://localhost:3000` |
| `env.BACKEND_INTERNAL_URL` | In-cluster URL the frontend uses to reach the backend | `http://backend:3000` |
| `env.UPLOAD_DIRECTORY` | Local filesystem path for uploaded media | `""` |
| `env.NEXT_PUBLIC_UPLOAD_STATIC_DIRECTORY` | Public path used to serve uploaded media | `""` |
| `env.NX_ADD_PLUGINS` | Nx plugin flag (leave as-is for most deployments) | `"false"` |
| `env.IS_GENERAL` | Enable general (self-host) mode | `"true"` |
| `env.TEMPORAL_ADDRESS` | **Required**: `host:port` of your Temporal server (this chart does not bundle one; unset falls back to `localhost:7233`, which fails in k8s) | `""` |
| `env.TEMPORAL_NAMESPACE` | Temporal namespace | `"default"` |

#### Secrets (`secrets`)

Every key below is stored in the chart's Secret. Leave a key empty to disable the corresponding feature; set only what you need.

| Parameter | Description | Default |
| --- | --- | --- |
| `secrets.DATABASE_URL` | PostgreSQL connection string used by the app | `""` |
| `secrets.REDIS_URL` | Redis connection string used by the app | `""` |
| `secrets.JWT_SECRET` | Secret used to sign auth tokens (**set a unique value**) | `""` |
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

> **The app always reads its database and cache endpoints from `secrets.DATABASE_URL` and `secrets.REDIS_URL`.** The chart does not auto-derive them from the bundled subcharts. With a release named `postqueen` and the default bundled services, they typically look like:
>
> ```yaml
> secrets:
>   DATABASE_URL: "postgresql://postqueen:postqueen-password@postqueen-postgresql:5432/postqueen"
>   REDIS_URL: "redis://:postqueen-redis-password@postqueen-redis-master:6379"
> ```

#### Example: a real deployment

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

### Parameters

The following tables list the configurable parameters of the chart and their defaults. Application settings (`env.*` and `secrets.*`) are documented separately under [Configuration](#configuration).

#### Core

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

#### Ingress

| Parameter | Description | Default |
| --- | --- | --- |
| `ingress.enabled` | Create an Ingress resource | `false` |
| `ingress.className` | IngressClass to use | `""` |
| `ingress.annotations` | Ingress annotations | `{}` |
| `ingress.hosts` | List of hosts, each with a nested `paths` list (`path`, `pathType`, `port`) | `[{host: chart-example.local, paths: [{path: /, pathType: Prefix, port: 80}]}]` |
| `ingress.tls` | TLS configuration | `[]` |
| `ingress.extraRules` | Additional raw ingress rules | `[]` |

#### Database & cache (bundled subcharts)

| Parameter | Description | Default |
| --- | --- | --- |
| `postgresql.enabled` | Deploy the bundled Bitnami PostgreSQL | `true` |
| `postgresql.auth.username` | Bundled PostgreSQL username | `postqueen` |
| `postgresql.auth.password` | Bundled PostgreSQL password | `postqueen-password` |
| `postgresql.auth.database` | Bundled PostgreSQL database name | `postqueen` |
| `redis.enabled` | Deploy the bundled Bitnami Redis | `true` |
| `redis.auth.password` | Bundled Redis password | `postqueen-redis-password` |

#### Storage, scheduling & extras

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

### External database and Redis

#### External database support

To connect PostQueen to a database outside the cluster (for example a managed service), set `postgresql.enabled: false` so the bundled PostgreSQL is not deployed, then point the app at your database with the **`secrets.DATABASE_URL`** connection string:

```yaml
postgresql:
  enabled: false

secrets:
  DATABASE_URL: "postgresql://user:password@db.example.com:5432/postqueen"
```

#### External Redis support

Similarly, set `redis.enabled: false` and provide your Redis endpoint through **`secrets.REDIS_URL`**:

```yaml
redis:
  enabled: false

secrets:
  REDIS_URL: "redis://:password@redis.example.com:6379"
```

#### Persistence

When the bundled subcharts are enabled, PostgreSQL and Redis each request a [Persistent Volume](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) via dynamic provisioning, so their data survives pod restarts. Uploaded media is stored on the app pod's `uploads-volume`, which defaults to an `emptyDir` (ephemeral). For durable uploads, either configure object storage with the `secrets.CLOUDFLARE_*` keys, or supply a persistent `extraVolumes`/`extraVolumeMounts` pair pointing at `/uploads`.

### Upgrading

#### To 1.1.0

The chart is published at `oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app`, and the default database/Redis credentials were renamed to `postqueen*`. If you installed a `1.0.x` release, install the new chart under the `postqueen` release name (or set `--set postgresql.auth.*` / `redis.auth.*` to keep your existing credentials).

#### To 1.0.0

This was the first major release of the Helm chart.

---

## 🧱 Tech stack

- **pnpm workspaces** (monorepo)
- **[Next.js](https://nextjs.org)** (React) for the frontend
- **[NestJS](https://nestjs.com)** for the backend API
- **[Prisma](https://www.prisma.io)** (default: PostgreSQL)
- **[Temporal](https://temporal.io)** for scheduling and publishing workers
- **Redis** for cache and queues
- **[Resend](https://resend.com)** for email notifications

---

## 🔑 Get your API key

You will need an API key to use the CLI, the MCP server, the SDK or the public API. It takes a minute:

1. Open **[app.postqueen.ai/settings](https://app.postqueen.ai/settings)** (or your own self-hosted instance).
2. Go to **Developers → Public API**.
3. Click **Reveal** to show your key.
4. Copy it and set it in your shell:

```bash
export POSTQUEEN_API_KEY="your_api_key"
```

Keep it secret: it grants full access to your account. You can revoke or rotate it any time from the same screen.

---

## 🛡️ Compliance

- PostQueen is an open-source, self-hostable social media scheduler that supports X, LinkedIn, Instagram, Bluesky, Mastodon, Discord and 30+ more.
- The hosted service uses official, platform-approved OAuth flows.
- PostQueen does not automate or scrape content from social media platforms.
- PostQueen does not collect, store, or proxy API keys or access tokens from users.
- PostQueen never asks users to paste social-platform credentials into the hosted product.
- Users always authenticate directly with each platform (X, LinkedIn, Discord, and so on), which keeps every platform's compliance and your data privacy intact.

---

## ❤️ Community & Support

We would love to hear from you, whether you hit a bug, have an idea, or just want to say hi:

- 🐛 **Found a bug or have a feature idea?** [Open an issue](https://github.com/GkhanKINAY/postqueen-app/issues).
- 💌 **Need a hand?** Email **support@postqueen.ai**.
- 📚 **Getting started?** The [docs](https://docs.postqueen.ai) walk you through everything.

If PostQueen saves you time, a ⭐ on the repo genuinely helps other people find it.

## 💜 Why we built PostQueen, and a thank you

We believe the way we work is about to change. AI is getting better every month, and before long, getting real work done by simply talking to an assistant will feel completely normal. We wanted to build something for that shift, in the spirit of tools we admire like [Chatbase](https://www.chatbase.co) and [Wispr Flow](https://wisprflow.ai).

Social media felt like the perfect place to start: it takes real time and effort, and most of it is work an assistant can carry for you. When we found that Nevo David had open-sourced [Postiz](https://github.com/gitroomhq/postiz-app) under AGPL-3.0, we knew we had the foundation we needed. [PostQueen](https://postqueen.ai) grows that work in its own direction: an assistant that runs your social media, so you can spend your time on everything else.

Thank you, Nevo David and the Postiz contributors. We could not have started this without you. 🙏💜

## License

This chart is licensed under the Apache License 2.0, see the [LICENSE](LICENSE) file for details. It is a fork of the [Postiz Helm chart](https://github.com/gitroomhq/postiz-helmchart) (Apache-2.0). Thanks to its original maintainers.
