# Persona Changelog

## 2026-05-31 00:03 PDT — May 30 homelab ops: Portainer, NPM/Pi-hole, Uptime Kuma, Wazuh

**File:** `Memory.md`

**Change:** Added three new entries under "Homelab Changes → Pirate Stack" documenting May 30 infrastructure work.

**Diff summary:**
```diff
+ - **Portainer deployed + full NPM/Pi-hole reconfiguration (May 30)** — Deployed Portainer on new CT 108 (10.2.7.111) with agents on pirate CT 103 and monitoring CT 106. Created 17 NPM proxy hosts with Let's Encrypt SSL: pirate services at `*.pirate.lan`, monitoring/cross-CT at `*.lan`. Configured Pi-hole with wildcard `*.pirate.lan` → 10.2.7.109 + individual `*.lan` records. Documented everything on Gitea.
+ - **Uptime Kuma migrated to CT 109 (May 30)** — Migrated standalone Uptime Kuma from monitoring CT (CT 106, where SQLite was locking from shared high-I/O disk) to new dedicated CT 109. Resolved SQLITE_BUSY locking errors.
+ - **Wazuh vulnerability detection verified (May 30)** — Confirmed Wazuh vulnerability detector already active out-of-the-box: 967 tracked vulnerabilities, 473 alerts fired, 60-min feed updates, covering all CTs including pirate stack. Dashboard at https://10.2.7.110 (admin / password from creds file).
```

## 2026-05-30 03:58 PDT — Media stack fix entry

**File:** `Memory.md`

**Change:** Added a new entry under the "Homelab Changes → Pirate Stack" section documenting the May 29 full media stack fix.

**Diff summary:**
```diff
+ - **Full media stack fix (May 29)** — Debugged and fixed FlareSolverr proxy in 
+   Prowlarr (missing proxy + tag linkage), added 1337x indexer with Cloudflare 
+   bypass, connected Bazarr to Sonarr via SignalR, mounted torrent directories into 
+   Jellyfin so manually-downloaded content appears. Result: anime (Golden Time, 3D 
+   Kanojo S1+S2, Toradora!) successfully downloading via Sonarr→qBittorrent→Jellyfin. 
+   Media stack fully operational with end-to-end automation.
```
