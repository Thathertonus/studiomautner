# 🧠 Infrastructure Notes — Studio Mautner

## System Overview
- Environment: WSL 2 (Ubuntu 24.04)
- Web server: Nginx
- Reverse proxy: Cloudflare Tunnel
- Website directory: `/var/www/studiomautner`
- Deployment scripts: `~/deploy/`
- Backup scripts: `~/deploy/backup-site.sh`

## Network
- Local IP: 172.20.22.114
- LAN Gateway: 192.168.0.1
- Public domain: home.studiomautner.com (via Cloudflare Tunnel)

## Security
- SSH: key-based auth only (planned)
- Firewall: UFW + Fail2Ban (to be configured on Pi)
- Automatic updates + SSL renewal: pending

## Migration Plan (to Raspberry Pi 5)
1. Flash Pi OS Lite 64-bit
2. Enable SSH + static IP
3. Clone `/var/www` and `/etc/nginx`
4. Copy `/home/mike/.cloudflared` and `~/deploy/`
5. Start tunnel and verify connectivity

## Logs
- Nginx logs: `/var/log/nginx/access.log`
- Tunnel logs: `/home/mike/.cloudflared/`
---

## ✅ Next Steps Checklist

### 🧩 Configuration & Deployment
[x] Nginx installed and serving locally  
[x] Deployment scripts created (`setup-nginx.sh`, `deploy-site.sh`, `setup-firewall.sh`)  
[x] Cloudflared installed and authenticated  
[x] Tunnel created (`studiomautner-tunnel`)  
[x] Cloudflare DNS propagation confirmed  
[x] HTTPS validated through Cloudflare  
[x] Public access verified at https://home.studiomautner.com  

### 🧰 Security & Maintenance
- [ ] Configure UFW and Fail2Ban (for Raspberry Pi)
- [ ] Enable SSH key-only authentication
- [ ] Set up automatic updates and log rotation
- [ ] Schedule nightly rsync backups to external drive

### 💾 Migration to Raspberry Pi 5
- [ ] Flash Pi OS Lite (64-bit)
- [ ] Enable SSH + static IP
- [ ] Copy Nginx configs and web files
- [ ] Copy `~/.cloudflared` and `~/deploy`
- [ ] Start tunnel and test public access

### 📊 Monitoring & Documentation
- [ ] Add Uptime Kuma or GoAccess for uptime tracking
- [ ] Document IPs, ports, and credentials (sanitized)
- [ ] Record hardware changes and performance metrics
- [ ] Test recovery from backup

---

## 🗓️ Daily Journal

## 2025-11-01 — Phase 2 Completion : Public Access Live
• Cloudflare Tunnel (`a2f9d7d3-af96-45c9-b3cc-eb8f057d925f`) active and healthy  
• Nginx serving `/var/www/studiomautner` locally via port 80  
• Cloudflare proxy routing confirmed — site reachable at https://home.studiomautner.com  
• Cloudflared service installed and enabled (systemd)  
• Local HTTPS validated on 8443; switched to HTTP backend for tunnel stability  
• DNS propagation verified  
• Next Phase → Migrate to Raspberry Pi 5 for 24/7 uptime + UFW/Fail2Ban hardening

