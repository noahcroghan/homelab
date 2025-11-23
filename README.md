# Homelab Configuration

A collection of Docker Compose and other files used to run my homelab

## Instructions

### Media Stack
In `media/`, change `.env.example` to `.env` and add the relevent Cloudflare API key and Homarr secret token in place of the variables. Similar changes are required to `Caddyfile-example`, which you should change to `Caddyfile` and configure properly if you intend to use Caddy to expose the services as subdomains of your domain of choice. I use A Records in Cloudflare pointing to my server's Tailscale IP address, making the services only accessible via Tailscale.

### Minecraft

In `minecraft/`, you should rename the provided `.env.example` to `.env` and add the Minecraft IGNs of user's you want to be whitelisted.
