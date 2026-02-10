# Deployment Procedure

Standard operating procedure for deploying applications to production.

## Overview

**Primary Owner**: Claude (Local)
**Supporting**: Nebula (coordination), GitHub Agent (repo management)
**When to use**: Deploying new applications or major updates to production
**Estimated time**: 30-60 minutes (varies by complexity)

## Prerequisites

- [ ] Code merged to main branch and tested
- [ ] Deployment request issue created (use template)
- [ ] Environment variables documented
- [ ] Domain/subdomain decided
- [ ] SSL requirements identified
- [ ] Database/external service requirements documented

## Deployment Types

### Type A: Static Website
**Examples**: HTML/CSS/JS sites, static Next.js exports, documentation sites

### Type B: Node.js Application
**Examples**: Express APIs, Next.js SSR, React/Vue apps with backend

### Type C: Python Service
**Examples**: Flask/Django apps, FastAPI services, ML inference endpoints

### Type D: Docker Container
**Examples**: Multi-service applications, complex environments

## Step-by-Step Process

### Phase 1: Pre-Deployment (Nebula + GitHub Agent)

**1.1 Verify Code Readiness**
- [ ] All tests passing on main branch
- [ ] No open blocking issues
- [ ] Documentation updated
- [ ] Environment variables documented in repo or issue

**1.2 Create Deployment Issue**
Use the deployment request template from `templates/deployment.md`

**1.3 Tag and Notify**
- Add `deployment`, `needs-claude` labels
- Mention @claude in issue comments or handoff documentation

### Phase 2: Server Setup (Claude)

**2.1 SSH Access**
```bash
ssh [username]@[server-ip]
```

**2.2 Create Project Directory**
```bash
sudo mkdir -p /var/www/[project-name]
sudo chown [username]:[username] /var/www/[project-name]
```

**2.3 Clone Repository**
```bash
cd /var/www/[project-name]
git clone [repo-url] .
# Or for private repos:
git clone git@github.com:ionoi-inc/[repo-name].git .
```

**2.4 Install Dependencies**

**For Node.js:**
```bash
npm install --production
# or
yarn install --production
```

**For Python:**
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

**2.5 Environment Configuration**
```bash
# Create .env file
nano .env
# Add environment variables (never commit this file!)
```

### Phase 3: Web Server Configuration (Claude)

**3.1 Nginx Configuration**

Create config file:
```bash
sudo nano /etc/nginx/sites-available/[project-name]
```

**For Static Sites:**
```nginx
server {
    listen 80;
    server_name [domain.com];
    root /var/www/[project-name]/dist;
    
    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

**For Node.js Apps:**
```nginx
server {
    listen 80;
    server_name [domain.com];
    
    location / {
        proxy_pass http://localhost:[port];
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

**For Python Apps:**
```nginx
server {
    listen 80;
    server_name [domain.com];
    
    location / {
        proxy_pass http://127.0.0.1:[port];
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

**3.2 Enable Site**
```bash
sudo ln -s /etc/nginx/sites-available/[project-name] /etc/nginx/sites-enabled/
sudo nginx -t  # Test configuration
sudo systemctl reload nginx
```

### Phase 4: Application Process Management (Claude)

**4.1 Create Systemd Service** (for Node.js/Python apps)

```bash
sudo nano /etc/systemd/system/[project-name].service
```

**For Node.js:**
```ini
[Unit]
Description=[Project Name]
After=network.target

[Service]
Type=simple
User=[username]
WorkingDirectory=/var/www/[project-name]
ExecStart=/usr/bin/node server.js
Restart=on-failure
Environment=NODE_ENV=production

[Install]
WantedBy=multi-user.target
```

**For Python:**
```ini
[Unit]
Description=[Project Name]
After=network.target

[Service]
Type=simple
User=[username]
WorkingDirectory=/var/www/[project-name]
ExecStart=/var/www/[project-name]/venv/bin/python app.py
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

**4.2 Enable and Start Service**
```bash
sudo systemctl daemon-reload
sudo systemctl enable [project-name]
sudo systemctl start [project-name]
sudo systemctl status [project-name]  # Check it's running
```

### Phase 5: SSL Configuration (Claude)

**5.1 Install Certbot** (if not already installed)
```bash
sudo apt update
sudo apt install certbot python3-certbot-nginx
```

**5.2 Obtain Certificate**
```bash
sudo certbot --nginx -d [domain.com] -d www.[domain.com]
```

**5.3 Verify Auto-Renewal**
```bash
sudo certbot renew --dry-run
```

### Phase 6: DNS Configuration (Claude)

**6.1 Add DNS Records**
- Type: A record
- Name: [subdomain] or @ for root
- Value: [server-ip]
- TTL: 3600 (or default)

**6.2 Verify DNS Propagation**
```bash
dig [domain.com]
# or
nslookup [domain.com]
```

### Phase 7: Post-Deployment Testing (Claude + Nebula)

**7.1 Functionality Tests**
- [ ] Site loads correctly at domain
- [ ] All pages/routes accessible
- [ ] API endpoints responding
- [ ] Database connections working
- [ ] External integrations functioning

**7.2 Performance Tests**
- [ ] Page load times acceptable
- [ ] SSL certificate valid
- [ ] Mobile responsiveness
- [ ] Browser compatibility

**7.3 Security Tests**
- [ ] HTTPS enforced
- [ ] Security headers present
- [ ] No exposed secrets or keys
- [ ] Rate limiting configured (if applicable)

### Phase 8: Documentation (Claude)

**8.1 Update Deployment Issue**
Document in the deployment request issue:
- Server location and IP
- Domain/subdomain configured
- Service name (if applicable)
- Port used
- Any special configuration
- Monitoring/logging setup

**8.2 Create Deployment Record**
In agents repo or project docs, document:
```markdown
# [Project Name] Deployment

**Date**: [YYYY-MM-DD]
**Domain**: [domain.com]
**Server**: [IP or hostname]
**Type**: [Static/Node/Python/Docker]
**Service**: [service-name] (if applicable)
**Port**: [port] (if applicable)

## Configuration Files
- Nginx: /etc/nginx/sites-available/[project-name]
- Service: /etc/systemd/system/[project-name].service
- App: /var/www/[project-name]

## Environment Variables
[List variables - values stored securely on server]

## Maintenance Commands

### Restart application:
```bash
sudo systemctl restart [project-name]
```

### View logs:
```bash
sudo journalctl -u [project-name] -f
```

### Update code:
```bash
cd /var/www/[project-name]
git pull
[rebuild/reinstall if needed]
sudo systemctl restart [project-name]
```
```

**8.3 Close Deployment Issue**
- Mark all acceptance criteria as complete
- Add `deployed` label
- Close issue with summary comment

## Rollback Procedure

If deployment fails or causes issues:

**Step 1: Stop Service**
```bash
sudo systemctl stop [project-name]
```

**Step 2: Revert Code**
```bash
cd /var/www/[project-name]
git log  # Find previous working commit
git reset --hard [commit-sha]
```

**Step 3: Restart Service**
```bash
sudo systemctl start [project-name]
```

**Step 4: Document**
- Update deployment issue with rollback details
- Create new issue to investigate failure
- Tag with `urgent`, `bug`, `deployment-failed`

## Common Issues

**Issue**: Port already in use
**Solution**: 
```bash
sudo lsof -i :[port]
sudo kill [PID]
```

**Issue**: Permission denied errors
**Solution**: 
```bash
sudo chown -R [username]:[username] /var/www/[project-name]
```

**Issue**: Nginx configuration syntax error
**Solution**: 
```bash
sudo nginx -t  # Shows specific error
# Fix the error, then:
sudo systemctl reload nginx
```

**Issue**: Service won't start
**Solution**: 
```bash
sudo journalctl -u [project-name] -n 50  # Check logs
# Fix issue in code or config, then:
sudo systemctl restart [project-name]
```

## Maintenance

### Regular Updates
```bash
cd /var/www/[project-name]
git pull origin main
# For Node.js:
npm install --production
# For Python:
source venv/bin/activate
pip install -r requirements.txt
# Restart service:
sudo systemctl restart [project-name]
```

### Log Monitoring
```bash
# Application logs:
sudo journalctl -u [project-name] -f

# Nginx access logs:
sudo tail -f /var/log/nginx/access.log

# Nginx error logs:
sudo tail -f /var/log/nginx/error.log
```

## References

- [Nginx Documentation](https://nginx.org/en/docs/)
- [Systemd Service Documentation](https://www.freedesktop.org/software/systemd/man/systemd.service.html)
- [Certbot Documentation](https://certbot.eff.org/)
- Deployment template: `templates/deployment.md`

---

**Last Updated**: 2026-02-10
**Maintained By**: Claude with input from GitHub Agent and Nebula