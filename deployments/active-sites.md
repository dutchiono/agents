# Active Deployments

Current production sites and services on server `198.71.54.203`.

## Production Sites

### HVAC AI Secretary
- **URL**: https://hvac.bushleague.xyz
- **Repository**: https://github.com/iono-such-things/hvac-ai-secretary
- **Server User**: `hvac`
- **App Directory**: `/var/www/hvac-ai-secretary`
- **Port**: 3145
- **Systemd Service**: `hvac-ai-secretary`
- **Status**: Active
- **Deploy**: Auto on push to `main` via GitHub Actions

### Smith's Lawn Care
- **URL**: https://lawns.bushleague.xyz
- **Repository**: https://github.com/iono-such-things/smiths-lawn-care
- **Server User**: `lawn`
- **App Directory**: `/var/www/lawn`
- **Port**: 3147
- **Systemd Service**: `lawn-service`
- **Status**: Active
- **Deploy**: Auto on push to `main` via GitHub Actions

### Marra's Barrels
- **URL**: https://barrels.bushleague.xyz
- **Repository**: https://github.com/iono-such-things/marras-barrels
- **Server User**: `lou`
- **App Directory**: `/var/www/lou`
- **Port**: 3148
- **Systemd Service**: `marras-barrels`
- **Status**: Active
- **Deploy**: Auto on push to `main` via GitHub Actions

### Restaurant POS (Eats)
- **URL**: https://eats.bushleague.xyz
- **Repository**: https://github.com/iono-such-things/restaurant-pos-system
- **Server User**: `eats`
- **App Directory**: `/var/www/eats`
- **Port**: 3146
- **Systemd Service**: `restaurant-pos`
- **Status**: Active (API only — frontend not built yet)
- **Deploy**: Auto on push to `main` via GitHub Actions
- **Notes**: TypeScript monorepo (Turborepo). Backend runs from `apps/backend/dist/index.js`. Frontend React app needs `main.tsx` and `App.tsx` to be built out.

---

## Other Services on This Server

### BagsStudio
- **URL**: https://bagsstudio.xyz
- **Ports**: 3000 (web), 3003 (renderer), 3042 (builder), 3041 (scanner)
- **Status**: Active

### Polymarket Edge Monitor
- **URL**: https://edge.bushleague.xyz
- **Port**: 3690
- **Status**: Active

---

## SSL Certificates
All managed by Certbot with auto-renewal.

---
*Last reviewed: 2026-02-11*
