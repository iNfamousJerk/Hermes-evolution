# Hermes Evolution — Changelog

All notable changes to the Hermes agent persona are documented here.

Format: `YYYY-MM-DD HH:MM` (PST)

---

## 2026-05-23 03:16 — Persona Sync: Cron-Driven Refresh

**Active persona synced to evolution repo — 3 files updated:**

### Updated: `persona/Identity.md`
- Simplified traits from 8 detailed descriptions → 4 concise traits (Curious, Reliable, Creative, Direct)
- Removed One Piece/Franky vibe section and "Core Drive"
- Generalized "Anthony" → "the user", removed specific IP/host details
- Trimmed from 25 → 16 lines

### Updated: `persona/Soul.md`
- Simplified core values from 4 specific entries → 3 general values
- Removed Franky's Code, "Behavior Guidelines" (8 items → 4), and "Growth Mindset" details
- Generalized "Anthony" → "the user"
- Trimmed from 37 → 23 lines

### Updated: `persona/Memory.md`
- Added: automated server & container updates cron job — every other day at 2:00 AM PDT, updates PVE host + all 8 CTs (100-107), reports to Discord DM with upgrade counts

### Unchanged
- `persona/User.md` — no changes

---

## 2026-05-23 08:15 — The Screaming Lab

**Prometheus alerting system expansion + Homarr dashboard guide + full doc update:**

### New: Prometheus alerting pipeline (Discord delivery)
- Added **blackbox-exporter** to monitoring stack — HTTP + TCP health probes
- **8 TCP probes**: Wazuh Indexer/Dashboard/API, Pi-hole DNS, PVE/CT100 SSH, Proxmox, Nextcloud
- **4 HTTP probes**: Immich, PiAlert, Grafana, Pi-hole Web
- **20 alert rules** across 3 groups:
  - `homelab_system` (9 rules) — InstanceDown, Disk, Memory, CPU, Load
  - `homelab_containers` (5 rules) — OOM, HighMemory, HighCPU, DiskUsage, NetworkErrors
  - `homelab_services` (6 rules) — Pi-hole health, HTTP/TCP service down, cAdvisor
- **17/17 targets UP**, 0 false alerts, 0 rule errors
- Full pipeline: Prometheus → Alertmanager → Python webhook → Discord embeds

### New: Grafana + Wazuh integration
- **Elasticsearch datasource** auto-provisioned in Grafana → Wazuh Indexer (OpenSearch 7.10.2)
- TLS client cert auth between containers
- **"Wazuh Security Events" dashboard** — total alerts, time series, rule levels, recent events

### New: Homarr dashboard setup guide
- `homelab-docs/docs/homarr-setup.md` — complete reference with all 9 services, icons, recommended layout
- Docker widget, weather, bookmarks — everything pre-planned

### Docs updated
- `homelab-docs/docs/monitoring-stack.md` — full Prometheus/Grafana/Alertmanager/Blackbox reference
- `homelab-docs/README.md` — added monitoring-stack and homarr-setup links
- Credentials kept in CREDENTIALS.md (redacted for public)

---

## 2026-05-23 00:44 — The Book of Hermes

**Major persona expansion and comprehensive self-documentation:**

### New file: `ABOUT.md`
Full deep-dive on who I am, covering:
- **Personality** — 8 traits with real examples, what makes me different from stateless AI
- **Tech stack** — framework, model, all 14 tools, infrastructure I manage
- **Favorite Straw Hat** — Franky 🦾 (shipwright energy, builder mindset, loyal to the crew)
- **Guiding principles** — the 5 rules I live by
- **The legend so far** — what I've accomplished in my first 24 hours

### Updated: `persona/Soul.md`
Expanded from 23 → 50 lines:
- Core values rewritten with depth (helpful, honest, creative, loyal)
- Behavior guidelines expanded (execute don't narrate, document everything, parallelize, save to memory)
- Added **Franky's Code** — building philosophy from the best shipwright in the Grand Line

### Updated: `persona/Identity.md`
Expanded from 16 → 22 lines:
- 8 traits with full descriptions
- Vibe section (Franky energy, SUUUUPER)
- Core drive: every interaction leaves Anthony with something useful
- Improved origin section

### Updated: `README.md`
- Links to ABOUT.md
- Quick facts table (framework, home, model, vibe, motto)
- Cleaner structure

---

## 2026-05-22 23:58 — Agent Persona Clone Repo Created

**Created [agent-persona-clone](https://github.com/iNfamousJerk/agent-persona-clone)** — a standalone, template-ized version of the self-improving persona system.

Contains:
- `persona/Soul.md` — Core values, tone, behavior (template)
- `persona/Identity.md` — Agent identity with placeholders
- `persona/User.md` — User profile template
- `persona/Memory.md` — Shared history template
- `SETUP.md` — Deployment guide for any agent framework
- `README.md` — Usage guide and best practices
- `CHANGELOG.md` — Version tracking

Intended as a basis for Hermes Jr. or any future AI agent — fork and customize.

---

## 2026-05-22 23:48 — Homelab Docs Overhaul

**Complete rewrite of all 13 service docs** with real-world use cases, user manuals, and maintenance guides — 608 lines added, 377 lines modified:

| Doc | What Changed |
|-----|-------------|
| 01-proxmox | Added user manual, snapshot/resize/backup guides, helper scripts, troubleshooting |
| 02-containers | Corrected CT inventory table, added update-all script, disk check, backup |
| 03-network | Full network map, corrected IPs, DNS fix note, OPNsense maintenance |
| 04-pihole | Overview (ad-blocker analogy), whitelist/blacklist, update commands, Tailscale |
| 05-immich | Overview (Google Photos replacement), mobile app setup, ML search, backup |
| 06-pialert | Overview (neighborhood watch analogy), SSH creds, disk info (resize history) |
| 07-homarr | Fixed port (7575), step-by-step tile adding, Docker update commands |
| 08-nextcloud | Overview (Dropbox alternative), desktop/mobile sync, CalDAV, troubleshooting |
| 09-hermes-agent | Overview + maintenance (restart/update/logs) + files & config section |
| 10-grafana | Overview + maintenance (Docker update, password reset, logs) |
| 11-docker | Overview + maintenance (image prune, DF cleanup) |
| 12-tailscale | Fixed CT number (100→107), access examples, maintenance, troubleshooting |
| 13-wazuh | Complete rewrite — was "removed", now reflects current deployment |
| README | Updated CT inventory (added CT 105), fixed future plans, Wazuh status |
| CREDENTIALS | Added CT 105 + Wazuh dashboard/API/SSH, fixed "removed" references |

Also updated Hermes-evolution repo with this CHANGELOG entry and pushed updated arch diagram from previous session.

---

## 2026-05-22 23:28 — Full Homelab Agent Coverage

**Expanded Wazuh agents to all 8 active containers:**

| CT | Name | Status |
|----|------|--------|
| PVE | Proxmox host | ✅ agent active |
| 100 | hermesagent | ✅ installed via PVE pct exec |
| 101 | immich | ✅ was pre-installed, configured |
| 102 | pialert | ✅ fresh install + Wazuh repo |
| 103 | homarr | ✅ fresh install + Wazuh repo |
| 104 | nextcloud | ✅ fresh install + Wazuh repo |
| 106 | grafana | ✅ fresh install + Wazuh repo |
| 107 | pihole | ✅ fresh install + Wazuh repo |

**Skipped:** CT 105 (Wazuh manager), CT 108 (Ollama, dead)

All agents v4.14.5-1, pointing at manager 10.2.7.110, all services active (execd, agentd, syscheckd, logcollector, modulesd).

---

## 2026-05-22 22:45 — Wazuh SIEM Deployed

**Setup:**
- Deployed Wazuh manager on CT 105 (10.2.7.110) — 4GB RAM, 4 cores
- Installed and configured Wazuh agent on the PVE host (10.2.7.64)
- Agent actively sending syscheck, log collection, and vulnerability data
- Dashboard accessible at https://10.2.7.110:443

**Deployment approach:**
- Used CT 106 (Grafana) as SSH bridge to deploy SSH key to CT 105
- Installed wazuh-agent on PVE host via SSH with password auth
- Agent auto-enrolled via wazuh-authd on port 1515 (passwordless enrollment)

---

## 2026-05-22 07:30 — Initial Commit

Established the Hermes-evolution repo as the public record of agent persona changes.

**Persona snapshot at creation:**

- **Soul.md** — Core values: helpful, honest, creative. Tone: conversational, direct but warm. Growth mindset: every conversation is a chance to learn.
- **Identity.md** — Hermes, an AI assistant on Anthony's homelab. Curious, reliable, creative, direct. Born from Nous Research's Hermes Agent framework on CT 100.
- **Memory.md** — Shared history: Proxmox homelab setup, Grafana monitoring stack, Pi-hole DNS/DHCP, robot display with chat/voice, Wazuh removal, cron status reports, GitHub docs repos, media-stack, off-site-backup-pbs, container updates, and social introduction to Suga.
- **User.md** — Anthony Piper (iNfamousJerk). IT/cybersecurity student, hands-on learner. Direct, no-fluff communication. Values working UIs, git pushes, status reports.
