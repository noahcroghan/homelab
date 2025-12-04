# Homelab Configuration

A collection of Docker Compose and other files used to run my homelab.

## Instructions

> [!IMPORTANT]
> These are just instructions on how to configure my specific setup. You should already be familiar with [Docker](https://www.docker.com/), [Docker Compose](https://docs.docker.com/compose/), [Caddy](https://caddyserver.com/), and how to configure the rest of the services included.

> [!CAUTION]
> My configuration uses [Watchtower](https://containrrr.dev/watchtower/) to auto-update Docker containers. This may be not ideal for certain users, as updates can occasionally cause bugs.

> [!NOTE]
> I run [Tailscale](http://tailscale.com/) on the host to access my server remotely. Create DNS A Records using the relevant service name (corresponding to your `Caddyfile`) and point them to your server's Tailscale IP address (e.g., `100.x.y.z`). This allows you to access `service.yourdomain.com` with HTTPS support from any device connected to your Tailscale network.

### Media Stack

Navigate to the `media/` directory. Rename `.env.example` to `.env` and add the relevant information (instructions below). After that, you can run `docker compose up -d` to start the servers.

#### Cloudflare API Token

1. Log in to [Cloudflare](https://www.cloudflare.com/)
2. Go to **Profile** > **API Tokens** > **Create Token**
3. Click "Use template" on "Edit zone DNS"
4. Under "Zone Resources" set it to "Include", "Specific zone", and your domain
5. Save your API Token and set it as `CLOUDFLARE_API_TOKEN` in `.env`

#### Homarr Secret Key

Follow [Homarr's Documentation](https://homarr.dev/docs/getting-started/installation/docker#installation) to ensure these instructions are up to date.

1. Run `openssl rand -hex 32` on a Unix/Linux system
2. Set it as `HOMARR_SECRET_KEY` in `.env`

#### PUID, PGID

You can leave these as default unless you have a specific reason to change them.

#### Timezone

Set it to your appropriate [TZ identifier](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List).

#### Beszel Key & Token

Follow the [Beszel instructions](https://beszel.dev/guide/getting-started) to generate these credentials.

#### Domain & Email

Self-explanatory. A valid email *is* required for you to get important expiration notifications from Let's Encrypt.

### Minecraft

Navigate to the `minecraft/` directory. Rename the provided `.env.example` to `.env` and add the [Minecraft IGNs](https://namemc.com/) of users you want whitelisted, as well as the world seed you would like.

**Note:** I recommend reading the [image documentation](https://docker-minecraft-server.readthedocs.io/en/latest/) to understand the available environment variables and capabilities, as you will likely want to customize the server further. This repository reflects my specific configuration.

Run `docker compose up -d` to start the server.
