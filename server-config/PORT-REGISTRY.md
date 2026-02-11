# Port Registry — Server 198.71.54.203

All port assignments for services running on the bushleague server. When onboarding a new app, assign the next available port and update this document.

## Assigned Ports

| Port | Service | Repo | User | Domain | Status |
|------|---------|------|------|--------|--------|
| 3000 | BagsStudio Web | bagsstudio | root | bagsstudio.xyz | Active |
| 3001 | *(reserved — legacy HVAC dev port)* | — | — | — | Reserved |
| 3003 | BagsStudio Renderer | bagsstudio | root | bagsstudio.xyz | Active |
| 3041 | BagsStudio Scanner | bagsstudio | root | bagsstudio.xyz | Active |
| 3042 | BagsStudio Builder | bagsstudio | root | bagsstudio.xyz | Active |
| 3145 | HVAC AI Secretary | hvac-ai-secretary | hvac | hvac.bushleague.xyz | Active |
| 3146 | Restaurant POS (Eats) | restaurant-pos-system | eats | eats.bushleague.xyz | Active |
| 3147 | Smith's Lawn Care | smiths-lawn-care | lawn | lawns.bushleague.xyz | Active |
| 3148 | Marra's Barrels | marras-barrels | lou | barrels.bushleague.xyz | Active |
| 3690 | Polymarket Edge Monitor | polymarket-edge-monitor | root | edge.bushleague.xyz | Active |

## Next Available Port: **3149**

## Onboarding a New App

1. Assign the next available port from this registry
2. Create a system user: `adduser --disabled-password --gecos "" <username>`
3. Clone repo to `/var/www/<dirname>` as the new user
4. Create `.env` with at minimum `PORT=<assigned port>` and `NODE_ENV=production`
5. Create systemd service (see template below)
6. Create nginx site config with SSL (use certbot)
7. Set GitHub secrets: `SERVER_HOST`, `SERVER_USER`, `SERVER_PASSWORD`
8. Create deploy workflow (`.github/workflows/deploy.yml`)
9. Update this port registry
10. Update `deployments/active-sites.md`

## Systemd Service Template

```ini
[Unit]
Description=<Service Name>
After=network.target

[Service]
Type=simple
User=<username>
WorkingDirectory=/var/www/<dirname>
ExecStart=/usr/bin/node server.js
Restart=always
RestartSec=10
Environment=NODE_ENV=production
Environment=PORT=<port>

[Install]
WantedBy=multi-user.target
```

## Deploy Workflow Template

```yaml
name: Deploy to Server

on:
  push:
    branches: [main]
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to server
        uses: appleboy/ssh-action@v1.0.0
        with:
          host: ${{ secrets.SERVER_HOST }}
          username: ${{ secrets.SERVER_USER }}
          password: ${{ secrets.SERVER_PASSWORD }}
          script: |
            set -e
            APP_DIR="/var/www/<dirname>"
            REPO_URL="https://github.com/iono-such-things/<repo>.git"

            if [ -d "$APP_DIR/.git" ]; then
              cd $APP_DIR
              git remote set-url origin $REPO_URL
              git fetch origin main
              git reset --hard origin/main
            else
              git clone $REPO_URL $APP_DIR
              cd $APP_DIR
            fi

            npm install --omit=dev

            if [ ! -f .env ]; then
              echo "PORT=<port>" > .env
              echo "NODE_ENV=production" >> .env
            fi

            sudo systemctl restart <service-name>
            sudo systemctl status <service-name> --no-pager
```

---
*Last updated: 2026-02-11*
