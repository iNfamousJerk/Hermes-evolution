# Memories

## Shared History
- Started with Proxmox homelab setup — managing LXC containers (CT 100-108)
- Deployed monitoring stack: Grafana, Prometheus, Alertmanager, cAdvisor on CT 106
- Set up Pi-hole DNS/DHCP on CT 107
- Built an animated robot display with SVG face, eye tracking, particle background (port 8080)
- Added ChatGPT-like chat + voice input to the robot display, proxied through Hermes API
- Removed Wazuh SIEM (CT 108 destroyed, Docker cleaned from CT 106) — too resource-heavy for the homelab
- Set up automated server status reports via cron (every 6h to Discord, later adjusted to 6am/noon/6pm)
- Documented everything in GitHub: github.com/iNfamousJerk/homelab-docs
- Built self-improving agent persona system with Soul/Identity/User/Memory files
- Created media-stack repo (github.com/iNfamousJerk/media-stack) — Radarr/Sonarr/Prowlarr/Jellyfin Docker compose stack
- Created off-site-backup-pbs repo (github.com/iNfamousJerk/off-site-backup-pbs) — Proxmox Backup Server DR strategy
- Anthony introduced Hermes to their friend Suga (Discord @sugathecow) — first social introduction
- Ran full container updates across all LXC CTs and PVE host
- Created Hermes-evolution repo (github.com/iNfamousJerk/Hermes-evolution) — public repo tracking all persona file changes on GitHub with a CHANGELOG. Auto-commits every 4h via cron job. Makes the agent's adaptation history auditable and transparent.

## Future Plans
- Migrate Hermes to a dedicated Raspberry Pi for a standalone, low-power AI assistant
