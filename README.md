<p align="center">
  <a href="https://postqueen.ai">
    <img src=".github/assets/header.svg?v=6" width="840" alt="PostQueen, the queen of your posts, your AI social media assistant" />
  </a>
</p>

<h3 align="center">
  <a href="https://postqueen.ai/agent">🆕 NEW: meet the PostQueen Agent, run your social media from Claude Code, ChatGPT, OpenClaw or Hermes »</a>
</h3>

<br/>

<p align="center">
  <strong>Stop doing social media yourself.</strong>
</p>

<p align="center">
  PostQueen is an AI employee for your social media. Tell her what to share, in one sentence. She writes the copy, designs the visual and schedules it on every channel you have. You just review the calendar.
</p>

<p align="center">
  <strong>Views on autopilot. Posts every day. Launches everywhere.</strong><br/>
  <em>All while you do your actual job.</em>
</p>

<p align="center">
  <strong><a href="https://postqueen.ai">PostQueen</a></strong> is the open-source alternative to <strong>Buffer, Hootsuite, Sprout Social</strong> and <strong>Later</strong>.
</p>

<br/>

<p align="center"><img src=".github/assets/divider.svg" width="840" alt="" /></p>

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

<br/>

<p align="center">
  <!-- CHANNEL ICONS: 30 individual imgs, natural flow, mobile-wrap -->
  <img src=".github/assets/channels/instagram.svg" height="44" alt="Instagram" /> <img src=".github/assets/channels/youtube.svg" height="44" alt="YouTube" /> <img src=".github/assets/channels/google-business.svg" height="44" alt="Google Business Profile" /> <img src=".github/assets/channels/dribbble.svg" height="44" alt="Dribbble" /> <img src=".github/assets/channels/linkedin.svg" height="44" alt="LinkedIn" /> <img src=".github/assets/channels/reddit.svg" height="44" alt="Reddit" /> <img src=".github/assets/channels/tiktok.svg" height="44" alt="TikTok" /> <img src=".github/assets/channels/facebook.svg" height="44" alt="Facebook" /> <img src=".github/assets/channels/pinterest.svg" height="44" alt="Pinterest" /> <img src=".github/assets/channels/threads.svg" height="44" alt="Threads" /> <img src=".github/assets/channels/x.svg" height="44" alt="X" /> <img src=".github/assets/channels/slack.svg" height="44" alt="Slack" /> <img src=".github/assets/channels/discord.svg" height="44" alt="Discord" /> <img src=".github/assets/channels/mastodon.svg" height="44" alt="Mastodon" /> <img src=".github/assets/channels/bluesky.svg" height="44" alt="Bluesky" /> <img src=".github/assets/channels/lemmy.svg" height="44" alt="Lemmy" /> <img src=".github/assets/channels/warpcast.svg" height="44" alt="Farcaster" /> <img src=".github/assets/channels/telegram.svg" height="44" alt="Telegram" /> <img src=".github/assets/channels/nostr.svg" height="44" alt="Nostr" /> <img src=".github/assets/channels/vk.svg" height="44" alt="VK" /> <img src=".github/assets/channels/devto.svg" height="44" alt="Dev.to" /> <img src=".github/assets/channels/medium.svg" height="44" alt="Medium" /> <img src=".github/assets/channels/hashnode.svg" height="44" alt="Hashnode" /> <img src=".github/assets/channels/wordpress.svg" height="44" alt="WordPress" /> <img src=".github/assets/channels/whop.svg" height="44" alt="Whop" /> <img src=".github/assets/channels/kick.svg" height="44" alt="Kick" /> <img src=".github/assets/channels/mewe.svg" height="44" alt="MeWe" /> <img src=".github/assets/channels/twitch.svg" height="44" alt="Twitch" /> <img src=".github/assets/channels/listmonk.svg" height="44" alt="Listmonk" /> <img src=".github/assets/channels/skool.svg" height="44" alt="Skool" />
</p>


<br/>

<p align="center"><img src=".github/assets/divider.svg" width="840" alt="" /></p>

<br/>

<h3 align="center">Schedule and generate posts with AI</h3>

<p align="center">
  <img src=".github/assets/calendar.svg" width="660" alt="The PostQueen calendar: a week of posts across your channels, with AI generation and drag to reschedule" />
</p>

<br/>

<p align="center">
  <strong>Free for 7 days in the cloud. Forever free on your own server.</strong>
</p>

<p align="center">
  <a href="https://postqueen.ai"><img src=".github/assets/cta-cloud.svg" height="52" alt="Start free for 7 days" /></a>
  &nbsp;&nbsp;
  <a href="https://github.com/GkhanKINAY/postqueen-docker-compose"><img src=".github/assets/cta-selfhost.svg" height="52" alt="Self-host it free" /></a>
</p>

<br/>

---

## ⚠️ Before you install

Two things people miss, and one convention worth knowing:

- **The chart does not bundle Temporal.** PostQueen uses [Temporal](https://temporal.io) for scheduling and publishing: the app reads `TEMPORAL_ADDRESS` (default `localhost:7233`, which fails inside a cluster). Run a Temporal server alongside the release, or point at an existing one, and set `env.TEMPORAL_ADDRESS` to its `host:port`. Without it the UI loads but scheduled publishing will not run.
- **Production needs a public HTTPS domain.** To connect real social accounts, expose the release through an ingress with TLS on a public domain, because the social networks send their OAuth callbacks there.
- **Different convention than Docker Compose.** This chart's defaults use in-cluster service URLs and ports 80/5000, while the docker-compose stack publishes on host port 4007. They are two different deployment conventions, so follow this README rather than the compose one.

---

## 🚀 Installing the chart

This Helm chart deploys the [PostQueen](https://postqueen.ai) application on a Kubernetes cluster. It ships the app together with optional bundled PostgreSQL and Redis subcharts, a ConfigMap for non-sensitive settings, and a Secret for credentials, so a full deployment can be configured entirely through `values.yaml`.

The chart is published under its chart name `postqueen-app` (set in [`Chart.yaml`](charts/postqueen/Chart.yaml)), which is why the OCI reference ends in `.../charts/postqueen-app`. In this repository the chart source lives in the `charts/postqueen/` directory, so install commands use the chart name `postqueen-app` while any local edit points at `charts/postqueen/values.yaml`.

### Prerequisites

- Kubernetes 1.19+
- Helm 3.0+
- PV provisioner support in the underlying infrastructure (if persistence is required)

### Install

The chart is distributed as an OCI artifact from the GitHub Container Registry, so **no `helm repo add` is required**.

To install the chart with the release name `postqueen`:

```bash
helm install postqueen oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app
```

This deploys PostQueen with the default configuration, including bundled PostgreSQL and Redis. Before exposing it publicly you should at minimum set a unique `secrets.JWT_SECRET` and the connection strings described in [Configuration](#-configuration).

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

---

## 🔧 Configuration

Application settings are split into two maps in `values.yaml`:

- **`env`**: non-sensitive values, rendered into a **ConfigMap**.
- **`secrets`**: credentials and connection strings, rendered into a **Secret**.

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
| `env.TEMPORAL_ADDRESS` | **Required**: `host:port` of your Temporal server (this chart does not bundle one; unset falls back to `localhost:7233`, which fails in k8s) | `""` |
| `env.TEMPORAL_NAMESPACE` | Temporal namespace | `"default"` |

### Secrets (`secrets`)

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

### Parameters

The following tables list the configurable parameters of the chart and their defaults. Application settings (`env.*` and `secrets.*`) are documented above.

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

#### Database and cache (bundled subcharts)

| Parameter | Description | Default |
| --- | --- | --- |
| `postgresql.enabled` | Deploy the bundled Bitnami PostgreSQL | `true` |
| `postgresql.auth.username` | Bundled PostgreSQL username | `postqueen` |
| `postgresql.auth.password` | Bundled PostgreSQL password | `postqueen-password` |
| `postgresql.auth.database` | Bundled PostgreSQL database name | `postqueen` |
| `redis.enabled` | Deploy the bundled Bitnami Redis | `true` |
| `redis.auth.password` | Bundled Redis password | `postqueen-redis-password` |

#### Storage, scheduling and extras

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

Specify parameters with the `--set key=value[,key=value]` argument, or with a values file via `-f custom-values.yaml`.

---

## 🗄️ External database and Redis

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

---

## ⬆️ Upgrading

### To 1.1.0

The chart is published at `oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app`, and the default database/Redis credentials were renamed to `postqueen*`. If you installed a `1.0.x` release, install the new chart under the `postqueen` release name (or set `--set postgresql.auth.*` / `redis.auth.*` to keep your existing credentials).

### To 1.0.0

This was the first major release of the Helm chart.

---

## 🐳 Prefer Docker Compose?

If you do not need Kubernetes, the same stack runs with a single command via [postqueen-docker-compose](https://github.com/GkhanKINAY/postqueen-docker-compose). The docs walk through both paths: [Kubernetes with Helm](https://docs.postqueen.ai/installation/kubernetes-helm) and [Docker Compose](https://docs.postqueen.ai/installation/docker-compose).

---

## 🦞 Meet her open agents: OpenClaw &amp; Hermes

The two open-source agents everyone is running right now both speak PostQueen natively. **OpenClaw** lives on your machine and answers you from any chat app. **Hermes** does that too — and give it one brief, it plans your whole week on its own. Both drive the same `postqueen` CLI.

<p align="center">
  <img src=".github/assets/open-agents.svg" width="660" alt="OpenClaw and Hermes running PostQueen: chat apps feed OpenClaw, a one-line brief feeds Hermes, both drive the postqueen CLI and posts land on the calendar" />
</p>

<a href="https://postqueen.ai/openclaw"><img src=".github/assets/spotlight-openclaw.svg" width="410" alt="OpenClaw: runs on your machine; message her from WhatsApp, Telegram, Slack or Discord — set-up guide" /></a> <a href="https://postqueen.ai/hermes-agent"><img src=".github/assets/spotlight-hermes.svg" width="410" alt="Hermes: the self-improving autonomous agent; one brief becomes a planned, verified week — set-up guide" /></a>

**Any other agent works too** — anything that can run a CLI command or call MCP can run your socials. [Agent guide »](https://postqueen.ai/agent)

<br/>

---

## 🌐 Publish everywhere

Write once, be everywhere. PostQueen publishes to **30+ networks** out of the box:

<p align="center">
  <img src=".github/assets/channels/instagram.svg" height="44" alt="Instagram" /> <img src=".github/assets/channels/youtube.svg" height="44" alt="YouTube" /> <img src=".github/assets/channels/google-business.svg" height="44" alt="Google Business Profile" /> <img src=".github/assets/channels/dribbble.svg" height="44" alt="Dribbble" /> <img src=".github/assets/channels/linkedin.svg" height="44" alt="LinkedIn" /> <img src=".github/assets/channels/reddit.svg" height="44" alt="Reddit" /> <img src=".github/assets/channels/tiktok.svg" height="44" alt="TikTok" /> <img src=".github/assets/channels/facebook.svg" height="44" alt="Facebook" /> <img src=".github/assets/channels/pinterest.svg" height="44" alt="Pinterest" /> <img src=".github/assets/channels/threads.svg" height="44" alt="Threads" /> <img src=".github/assets/channels/x.svg" height="44" alt="X" /> <img src=".github/assets/channels/slack.svg" height="44" alt="Slack" /> <img src=".github/assets/channels/discord.svg" height="44" alt="Discord" /> <img src=".github/assets/channels/mastodon.svg" height="44" alt="Mastodon" /> <img src=".github/assets/channels/bluesky.svg" height="44" alt="Bluesky" /> <img src=".github/assets/channels/lemmy.svg" height="44" alt="Lemmy" /> <img src=".github/assets/channels/warpcast.svg" height="44" alt="Farcaster" /> <img src=".github/assets/channels/telegram.svg" height="44" alt="Telegram" /> <img src=".github/assets/channels/nostr.svg" height="44" alt="Nostr" /> <img src=".github/assets/channels/vk.svg" height="44" alt="VK" /> <img src=".github/assets/channels/devto.svg" height="44" alt="Dev.to" /> <img src=".github/assets/channels/medium.svg" height="44" alt="Medium" /> <img src=".github/assets/channels/hashnode.svg" height="44" alt="Hashnode" /> <img src=".github/assets/channels/wordpress.svg" height="44" alt="WordPress" /> <img src=".github/assets/channels/whop.svg" height="44" alt="Whop" /> <img src=".github/assets/channels/kick.svg" height="44" alt="Kick" /> <img src=".github/assets/channels/mewe.svg" height="44" alt="MeWe" /> <img src=".github/assets/channels/twitch.svg" height="44" alt="Twitch" /> <img src=".github/assets/channels/listmonk.svg" height="44" alt="Listmonk" /> <img src=".github/assets/channels/skool.svg" height="44" alt="Skool" />
</p>

| Category | Networks |
| --- | --- |
| **Major social** | X, LinkedIn, Instagram, Facebook, TikTok, YouTube, Threads, Pinterest, Reddit, Bluesky |
| **Community and chat** | Discord, Slack, Telegram, Mastodon, Twitch, Kick, MeWe, VK |
| **Publishing and blogs** | WordPress, Medium, Dev.to, Hashnode, Tumblr, Listmonk, Moltbook |
| **Web3 and decentralized** | Nostr, Farcaster, Lemmy |
| **Creator and business** | Google Business Profile, Whop, Skool, Dribbble |

LinkedIn and Instagram each support both personal and page posting. New connectors ship regularly: see the full list with per-network guides at [postqueen.ai/channels](https://postqueen.ai/channels).

<br/>

---

## ❤️ Community and support

- 🐛 **Found a bug or have an idea?** [Open an issue](https://github.com/GkhanKINAY/postqueen-helmchart/issues).
- 💌 **Need a hand?** Email **support@postqueen.ai**.
- 📚 **Getting started?** The [docs](https://docs.postqueen.ai) walk you through everything.

If PostQueen saves you time, a ⭐ on the repo genuinely helps other people find it.

<br/>

---

## 🙏 Thank you, Postiz

PostQueen is a fork of [Postiz](https://github.com/gitroomhq/postiz-app) by Nevo David, released under AGPL-3.0. Postiz gave us a rock-solid open-source scheduler: the connectors, the calendar, the Temporal pipeline, years of careful work that we did not have to redo. We forked it because we wanted to take that foundation in a specific direction, a social media manager you talk to instead of operate, and building on Postiz let us start from something that already worked.

Thank you, Nevo David and every Postiz contributor. This project exists because you chose to open-source yours. If PostQueen is not quite what you need, [Postiz](https://postiz.com) itself might be, and it deserves your star too. 🙏

<br/>

---

## 👑 The PostQueen ecosystem

| Repository | What lives there |
| --- | --- |
| [postqueen-app](https://github.com/GkhanKINAY/postqueen-app) | The application itself: frontend, backend, workers |
| [postqueen-agent](https://github.com/GkhanKINAY/postqueen-agent) | Agent CLI and skill: give any AI assistant hands |
| [postqueen-docker-compose](https://github.com/GkhanKINAY/postqueen-docker-compose) | Self-host the whole stack with one command |
| [postqueen-helmchart](https://github.com/GkhanKINAY/postqueen-helmchart) | Run it on Kubernetes |
| [postqueen-n8n](https://github.com/GkhanKINAY/postqueen-n8n) | The n8n community node for no-code automation |
| [postqueen-docs](https://github.com/GkhanKINAY/postqueen-docs) | Source of [docs.postqueen.ai](https://docs.postqueen.ai) |

On npm: [`postqueen`](https://www.npmjs.com/package/postqueen) (CLI) · [`@postqueen/node`](https://www.npmjs.com/package/@postqueen/node) (SDK) · [`n8n-nodes-postqueen`](https://www.npmjs.com/package/n8n-nodes-postqueen) (n8n)

<br/>

<p align="center">
  <strong>Long live the queen.</strong> 👑
</p>

<p align="center">
  <a href="https://postqueen.ai"><img src=".github/assets/cta-cloud.svg" height="52" alt="Start free for 7 days" /></a>
  &nbsp;&nbsp;
  <a href="https://github.com/GkhanKINAY/postqueen-docker-compose"><img src=".github/assets/cta-selfhost.svg" height="52" alt="Self-host it free" /></a>
</p>

## License

This chart is licensed under the Apache License 2.0, see the [LICENSE](LICENSE) file for details. It is a fork of the [Postiz Helm chart](https://github.com/gitroomhq/postiz-helmchart) (Apache-2.0). Thanks to its original maintainers.
