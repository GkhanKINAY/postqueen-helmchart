<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset=".github/assets/banner-dark.png">
    <img src=".github/assets/banner-light.png" width="100%" alt="PostQueen Helm chart. Run PostQueen on Kubernetes, with PostgreSQL and Redis inside the release or your own, pointed at a Temporal server.">
  </picture>
</p>

<p align="center">
  Helm chart for self-hosting PostQueen on Kubernetes. It needs a Temporal server; PostgreSQL and Redis can run inside the release or come from your own services.
</p>

<p align="center">
  <a href="https://postqueen.ai"><b>Website</b></a> ·
  <a href="https://docs.postqueen.ai/installation/kubernetes-helm"><b>Docs</b></a> ·
  <a href="https://postqueen.ai/pricing"><b>Pricing</b></a> ·
  <a href="https://github.com/GkhanKINAY/postqueen-helmchart/pkgs/container/postqueen-helmchart%2Fcharts%2Fpostqueen-app"><b>Chart package</b></a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-2563EB?labelColor=15131C" alt="License: Apache-2.0"></a>
  <a href="charts/postqueen/Chart.yaml"><img src="https://img.shields.io/badge/chart-1.1.6-0EA5E9?labelColor=15131C&logo=helm&logoColor=white" alt="Chart version 1.1.6"></a>
</p>

<p align="center">
  <a href="https://docs.postqueen.ai/agents/grok-bot"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/announce-dark.png"><img src="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/announce-light.png" width="100%" alt="New: Grok Bot is here. Connect Claude, ChatGPT, Grok Bot or any AI agent to your socials."></picture></a>
</p>

<p align="center">
  <a href="https://app.postqueen.ai/auth?utm_source=github&utm_medium=readme&utm_campaign=postqueen-helmchart&utm_content=hero-button"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/btn-trial-dark.png"><img src="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/btn-trial-light.png" width="323" alt="Start 7-day trial for $0"></picture></a><a href="https://docs.postqueen.ai/agents/overview"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/btn-agent-dark.png"><img src="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/btn-agent-light.png" width="297" alt="Connect your AI agent"></picture></a>
</p>

<p align="center">
  <sub><b>$0 due today.</b> A card is required, and you pay nothing if you cancel within 7 days.</sub>
</p>

<p align="center">
  <a href="https://github.com/GkhanKINAY/postqueen-helmchart/stargazers"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/star-dark.png"><img src="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/star-light.png" width="380" alt="Like PostQueen? Star the repo. It helps others find it."></picture></a>
</p>

<p align="center">
  <a href="https://docs.postqueen.ai/agents/overview"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/works-dark.png"><img src="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/works-light.png" width="100%" alt="Use the agent you already have: Claude, ChatGPT, Grok Bot (new), Grok, Perplexity, Muse (new), Claude Code, Codex, Cursor, Gemini CLI, VS Code, Devin Desktop, Zed, OpenClaw, Hermes, NanoClaw, Paperclip and any MCP app. Posts to 30+ networks."></picture></a>
</p>



<p align="center"><b>Run it on your cluster, or skip the servers?</b> PostQueen Cloud is the same app, run for you, so you can post today instead of waiting weeks for each network to approve an app of your own.</p>

<p align="center">
  <a href="https://app.postqueen.ai/auth?utm_source=github&utm_medium=readme&utm_campaign=postqueen-helmchart&utm_content=choose-cloud"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/choose-cloud-dark.png"><img src="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/choose-cloud-light.png" width="49%" alt="PostQueen Cloud, recommended: post today, not after the API reviews. PostQueen's own network apps, the hosted MCP server, AI included, updates and support handled. Start 7-day trial for $0, $0 due today."></picture></a>
  <a href="#quick-start"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/choose-self-dark.png"><img src="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/choose-self-light.png" width="49%" alt="Self-hosted, AGPL-3.0: run it on your own servers with PostgreSQL, Redis and Temporal, create a developer app on every network and wait for its review, bring your own AI keys, and handle updates yourself."></picture></a>
</p>

## What it does

- Deploys the all-in-one PostQueen image, `ghcr.io/gkhankinay/postqueen-app`: the web app, the API and the publishing workers in one pod, on container port 5000 behind a Service on port 80.
- Renders `env` into a ConfigMap and `secrets` into a Secret, and loads both into the app as environment variables.
- Deploys the Bitnami PostgreSQL and Redis subcharts by default, with their images from `bitnamilegacy/` on Docker Hub. Turn either off to use your own.
- Adds an Ingress when you enable it.
- Does not include Temporal. You point the app at your own Temporal server.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset=".github/assets/architecture-dark.png">
  <img src=".github/assets/architecture-light.png" width="100%" alt="Diagram of the Helm release. The browser reaches an optional Ingress, then the Service on port 80, then the postqueen-app pod on port 5000, which holds the web app, the API, the workers and its settings. The pod uses the optional PostgreSQL and Redis subcharts or your own, and reaches a Temporal server outside the chart through env.TEMPORAL_ADDRESS.">
</picture>

[PostQueen](https://github.com/GkhanKINAY/postqueen-app) is a social media scheduler with an AI copilot that posts to 30+ networks. It is open source under AGPL-3.0, and this chart runs it on your own cluster.

## Before you install

- **Temporal is required.** PostQueen schedules and publishes through [Temporal](https://temporal.io). Set `env.TEMPORAL_ADDRESS` to your Temporal server's `host:port`. Without it, the app falls back to `localhost:7233`, the UI loads, and scheduled posts never go out.
- **Real accounts need a public HTTPS domain.** Social networks send their sign-in callbacks there, so expose the release through an Ingress with TLS.
- **Uploads need a location.** The chart leaves `env.UPLOAD_DIRECTORY` empty, and with the default local storage the app does not start without it. The quick start below sets it to `/uploads`, where the chart mounts a volume.
- **Ports differ from Docker Compose.** The Service is port 80 to container port 5000. Leave `env.FRONTEND_URL` and `env.NEXT_PUBLIC_BACKEND_URL` empty until you have that domain, then set them to it. Do not copy Compose's `localhost:4007`.

## Quick start

The chart is published as an OCI artifact on the GitHub Container Registry, so there is no `helm repo add` step. Its name is `postqueen-app`; in this repository it lives in `charts/postqueen/`.

Write a `my-values.yaml`:

```yaml
env:
  TEMPORAL_ADDRESS: "temporal-frontend.temporal.svc:7233"   # your Temporal server
  FRONTEND_URL: "https://social.example.com"
  NEXT_PUBLIC_BACKEND_URL: "https://social.example.com/api"
  STORAGE_PROVIDER: "local"
  UPLOAD_DIRECTORY: "/uploads"
  NEXT_PUBLIC_UPLOAD_STATIC_DIRECTORY: "uploads"
secrets:
  JWT_SECRET: "a-long-random-string"
  ENCRYPTION_KEY: "another-long-random-string"
  DATABASE_URL: "postgresql://postqueen:postqueen-password@postqueen-postgresql:5432/postqueen"
  REDIS_URL: "redis://:postqueen-redis-password@postqueen-redis-master:6379"
```

Then install it:

```bash
helm install postqueen oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app \
  --version 1.1.6 -f my-values.yaml
```

The app always reads `secrets.DATABASE_URL` and `secrets.REDIS_URL`; the chart does not derive them from the subcharts. The values above match a release named `postqueen` with the bundled databases and their default passwords. Change those passwords in `postgresql.auth` and `redis.auth` for a real install.

## Configuration

Every key under `env` and `secrets` becomes an environment variable in the app, so you can add any setting from the [configuration reference](https://docs.postqueen.ai/configuration/reference), such as each network's client ID and secret.

| Value | Default | What it does |
| --- | --- | --- |
| `env.TEMPORAL_ADDRESS` | `""` | Your Temporal server's `host:port`. Required. |
| `env.TEMPORAL_NAMESPACE` | `default` | Temporal namespace |
| `env.FRONTEND_URL` | `""` | Public address of the app |
| `env.NEXT_PUBLIC_BACKEND_URL` | `""` | Public API address, the same host plus `/api` |
| `env.STORAGE_PROVIDER` | not set, so `local` | Where uploaded media is kept: `local` or `cloudflare` |
| `env.UPLOAD_DIRECTORY` | `""` | Folder for uploads with local storage. Required for `local`; use `/uploads`. |
| `env.NEXT_PUBLIC_UPLOAD_STATIC_DIRECTORY` | `""` | Path the web app serves uploads from; use `uploads` |
| `env.BACKEND_INTERNAL_URL` | `http://localhost:3000` | How the web app reaches the API inside the same container. Leave it as it is. |
| `secrets.JWT_SECRET` | `""` | Signs login sessions. Set a long random value. |
| `secrets.ENCRYPTION_KEY` | not set | Encrypts stored secrets, such as the app passwords and keys typed in when a channel is connected. Falls back to `JWT_SECRET` when unset. |
| `secrets.DATABASE_URL` | `""` | PostgreSQL connection string |
| `secrets.REDIS_URL` | `""` | Redis connection string |
| `image.repository` | `ghcr.io/gkhankinay/postqueen-app` | App image |
| `image.tag` | `latest` | App version. Pin one of the app's [releases](https://github.com/GkhanKINAY/postqueen-app/releases), such as `v3.6.84`. |
| `postgresql.enabled` | `true` | Deploy the bundled PostgreSQL |
| `postgresql.image.repository` | `bitnamilegacy/postgresql` | Bundled PostgreSQL image, tag `16.4.0-debian-12-r7` |
| `redis.enabled` | `true` | Deploy the bundled Redis |
| `redis.image.repository` | `bitnamilegacy/redis` | Bundled Redis image, tag `7.4.0-debian-12-r2` |
| `ingress.enabled` | `false` | Create an Ingress; set `ingress.hosts` and `ingress.tls` with it |
| `extraVolumes`, `extraVolumeMounts` | `[]` | The chart mounts an `emptyDir` at `/uploads` unless you mount your own volume there |

[`values.yaml`](charts/postqueen/values.yaml) lists every value with its default.

**Your own databases.** Set `postgresql.enabled: false` or `redis.enabled: false`, and point `secrets.DATABASE_URL` or `secrets.REDIS_URL` at your service.

**Uploads.** The default `emptyDir` is lost when the pod restarts. Mount a persistent volume at `/uploads`, or store media in Cloudflare R2: set `env.STORAGE_PROVIDER` to `cloudflare` and add the `CLOUDFLARE_*` keys from the [configuration reference](https://docs.postqueen.ai/configuration/reference).

### Upgrading

```bash
helm upgrade postqueen oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app \
  --version 1.1.6 -f my-values.yaml
```

- **1.1.6:** `appVersion` names the current app release, `v3.6.84`.
- **1.1.5:** `appVersion` named `v3.6.81`.
- **1.1.4:** local uploads work out of the box: `STORAGE_PROVIDER`, `UPLOAD_DIRECTORY` and `NEXT_PUBLIC_UPLOAD_STATIC_DIRECTORY` now default to the same values as the Docker Compose stack (`local`, `/uploads`, `uploads`), so the app no longer stops at start when they are left unset.
- **1.1.3:** the bundled PostgreSQL and Redis images come from `bitnamilegacy/` with the same tags, because Docker Hub no longer serves them under `bitnami/`. Releases that set their own `postgresql.image` or `redis.image` are not affected.
- **1.1.2:** `env.FRONTEND_URL` and `env.NEXT_PUBLIC_BACKEND_URL` default to empty, and `env.BACKEND_INTERNAL_URL` to `http://localhost:3000`. Releases that already set these keys keep their values.
- **1.1.1:** `appVersion` names a published app tag, `v3.6.0`. `image.tag` still defaults to `latest`.
- **1.1.0:** the chart moved to `oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app`, and the bundled database credentials were renamed to `postqueen*`. From 1.0.x, install under the release name `postqueen`, or set `postgresql.auth.*` and `redis.auth.*` to keep your old credentials.

`helm uninstall postqueen` removes the release. The volumes of the bundled PostgreSQL and Redis stay until you delete their PVCs.

Prefer a single host? [postqueen-docker-compose](https://github.com/GkhanKINAY/postqueen-docker-compose) runs the same image with Temporal included. Prefer not to run a server at all? The hosted service at [postqueen.ai](https://postqueen.ai) does it for you: [start a 7-day trial, $0 due today](https://app.postqueen.ai/auth?utm_source=github&utm_medium=readme&utm_campaign=postqueen-helmchart&utm_content=quick-start).

## Privacy and security

- Channels connect through each network's official OAuth sign-in where the network offers one. On your own cluster, that is the developer app you create for each network.
- Some networks, such as Bluesky, Lemmy, WordPress and Nostr, need an app password, an account password or a key that you paste in.
- Your instance stores these credentials in its database so it can post for you, and replaces them when you remove the channel.
- For the hosted service, read the [privacy policy](https://postqueen.ai/privacy-policy), or [delete your account](https://postqueen.ai/delete-my-account).

**Rather not run a cluster?** PostQueen Cloud is the same app, run for you: PostQueen's own network apps (no developer app reviews on your side), the hosted MCP server, AI credits and automatic updates.

<p align="center">
  <a href="https://app.postqueen.ai/auth?utm_source=github&utm_medium=readme&utm_campaign=postqueen-helmchart&utm_content=closing-band"><picture><source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/cta-dark.png"><img src="https://raw.githubusercontent.com/GkhanKINAY/postqueen-app/main/.github/assets/showcase/cta-light.png" width="100%" alt="Ready when you are: hand your next post to your agent. Start 7-day trial for $0. $0 due today, cancel in one click."></picture></a>
</p>

## Links

| | |
| --- | --- |
| Docs | [Kubernetes guide](https://docs.postqueen.ai/installation/kubernetes-helm) · [configuration reference](https://docs.postqueen.ai/configuration/reference) |
| Chart | `oci://ghcr.io/gkhankinay/postqueen-helmchart/charts/postqueen-app` |
| Repositories | [app](https://github.com/GkhanKINAY/postqueen-app) · [CLI and skill](https://github.com/GkhanKINAY/postqueen-agent) · [n8n node](https://github.com/GkhanKINAY/postqueen-n8n) · [docs](https://github.com/GkhanKINAY/postqueen-docs) · [Docker Compose](https://github.com/GkhanKINAY/postqueen-docker-compose) · [Helm chart](https://github.com/GkhanKINAY/postqueen-helmchart) |
| Help | support@postqueen.ai · [GitHub issues](https://github.com/GkhanKINAY/postqueen-helmchart/issues) |

## License

This chart is open source under the [Apache-2.0 license](LICENSE). PostQueen started as a fork of [Postiz](https://github.com/gitroomhq/postiz-app) by Nevo David, and this chart started from [postiz-helmchart](https://github.com/gitroomhq/postiz-helmchart).
