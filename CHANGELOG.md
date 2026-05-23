# Hermes Evolution — Changelog

All notable changes to the Hermes agent persona are documented here.

Format: `YYYY-MM-DD HH:MM` (PST)

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
