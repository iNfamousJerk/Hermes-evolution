# Memories

## Shared History
- Started with Proxmox homelab setup — managing LXC containers (CT 100-108)
- Deployed monitoring stack: Grafana, Prometheus, Alertmanager, cAdvisor on CT 106
- Set up Pi-hole DNS/DHCP on CT 107
- Built an animated robot display with SVG face, eye tracking, particle background (port 8080)
- Added ChatGPT-like chat + voice input to the robot display, proxied through Hermes API
- Removed Wazuh SIEM (original CT 108 destroyed, Docker cleaned from CT 106) — too resource-heavy for the homelab
- Set up automated server status reports via cron (every 6h to Discord, later adjusted to 6am/noon/6pm)
- Documented everything in GitHub: github.com/iNfamousJerk/homelab-docs
- Built self-improving agent persona system with Soul/Identity/User/Memory files
- Created media-stack repo (github.com/iNfamousJerk/media-stack) — Radarr/Sonarr/Prowlarr/Jellyfin Docker compose stack
- Created off-site-backup-pbs repo (github.com/iNfamousJerk/off-site-backup-pbs) — Proxmox Backup Server DR strategy
- Anthony introduced Hermes to their friend Suga (Discord @sugathecow) — first social introduction
- Ran full container updates across all LXC CTs and PVE host
- Created Hermes-evolution repo (github.com/iNfamousJerk/Hermes-evolution) — public repo tracking all persona file changes on GitHub with a CHANGELOG. Auto-commits every 4h via cron job.
- Ran comprehensive homelab documentation audit — professionalized all docs to enterprise standards across 6 pillars (networking, IAM, storage/DR, monitoring/SIEM, virtualization, docs/change control). Created NETWORK-TOPOLOGY.md, SOP-BACKUP-RESTORE.md, CHANGELOG.md, ACTION-PLAN.md. Pushed to GitHub + Gitea.
- Pirate CT: Originally CT 108 (stopped). Stack migrated to restored CT 103 — Gluetun VPN + qBittorrent, Prowlarr, Radarr, Sonarr, Lidarr, Bazarr, Jellyfin, Jellyseerr, Flaresolverr, Nginx Proxy Manager. 12 services, VPN-gated. Credentials: root/hoistthecolors, IP 10.2.7.109.  
- Docker bridge networking for Pirate stack: all *arr containers communicate via hostname except qBittorrent (in Gluetun namespace) which uses bridge IP 172.19.0.1:8080
- All container passwords standardized to lowercase
- **Full media stack fix (May 29)** — Debugged and fixed FlareSolverr proxy in Prowlarr (missing proxy + tag linkage), added 1337x indexer with Cloudflare bypass, connected Bazarr to Sonarr via SignalR, mounted torrent directories into Jellyfin so manually-downloaded content appears. Result: anime (Golden Time, 3D Kanojo S1+S2, Toradora!) successfully downloading via Sonarr→qBittorrent→Jellyfin. Media stack fully operational with end-to-end automation.

## Homelab Changes
- PiAlert CT 102 resized 2GB → 5GB via Proxmox API — disk was 79% full, now sits at 31% (3.3GB free)
- Created homelab-architecture repo (github.com/iNfamousJerk/homelab-architecture) — dark-themed SVG diagram of the full homelab stack
- PVE host root password: 2proxtheworld (different from container passwords)
- Automated server & container updates cron job — every other day at 2:00 AM (PDT), updates PVE host + all 8 CTs (100-107). Reports back to Discord DM with per-machine upgrade counts, failures, and reboot status.
- **Wazuh re-deployed on CT 108** — Wazuh manager at 10.2.7.110 with 10 active agents (PVE host + CTs 100-108). Dashboard HTTPS on port 443, API on 55000, enrollment port 1515. Integrated with Suricata IDS on OPNsense via syslog forwarding (UDP 514).
- **UPS monitoring stack deployed** — NUT (CyberPower CP1500 AVR) on PVE host with USB driver, Prometheus NUT exporter on CT 106, Grafana provisioned dashboard, Alertmanager with Discord webhook alerts. Graceful shutdown script at `/usr/local/bin/pve-ups-shutdown` stops containers, signals UPS to kill power, then shuts down host.
- **Container startup order configured** — Pi-hole (CT 107) first (delay 0), Grafana stack (CT 106) second (delay 30s), others (CT 100-105) third (delay 60s). All set to `onboot: 1`.

## Future Plans
- Migrate Hermes to a dedicated Raspberry Pi for a standalone, low-power AI assistant
- Build PBS second node on Dell Optiplex 7050 MT with 4 HDD ZFS mirrors ("Pirate PBS")
- R stack / PVE2 migration when hardware arrives