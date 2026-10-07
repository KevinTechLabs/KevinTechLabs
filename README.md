# 👋 Hey, I'm Kevin Marcotte

### Homelab Builder | Security & Blue Team | DevSecOps | Linux

I build my own infrastructure, attack it, lock it down, and write up exactly how it works.

Everything here started as a problem in my own homelab: a flat network anyone could cross, alerts nobody could trust, deploys done by hand. Each repo is how I fixed one of them, with the real numbers and the mistakes left in.

---

## 🛡️ What I focus on

- **Network defense:** pfSense with Suricata IDS and pfBlockerNG, VLAN segmentation, forced DNS through Pi-hole
- **Detection & response:** a Wazuh SIEM with evidence-based tuning, plus Sentinel, the SOC dashboard I wrote
- **Hardening:** CIS benchmarks, ufw and fail2ban, Docker exposure control, key-only SSH
- **DevSecOps:** CI/CD with SAST, image scanning, SBOMs, signed images and GitOps deploys that roll back on their own
- **Self-hosting & privacy:** local AI, encrypted notes and remote access over Tailscale only, with nothing exposed to the internet

---

## 🧪 My Home Lab Stack

Everything lives in a 10-inch, 8U desk rack. Full build and network docs: **[Desk-Pi-Rack](https://github.com/KevinTechLabs/Desk-Pi-Rack)**

### 🔒 Network & Security
- **Firewall:** Intel J1900 mini PC (4× Intel i210) running **pfSense** + **Suricata** + **pfBlockerNG**
- **Segmentation:** five VLAN zones (Servers, Trusted, Gaming & IoT, Lab, Guest); IoT, Lab and Guest get internet and DNS only
- **Switching & Wi-Fi:** TP-Link TL-SG108E (802.1Q), GL.iNet Flint 3 (Wi-Fi 7) with one network name per zone
- **DNS:** Raspberry Pi 5 running **Pi-hole**, upstream to pfSense's DNSSEC-validating resolver

### 📊 SIEM / SOC
- **Wazuh** manager, indexer and dashboard in Docker, with 5 agents (Windows 11 + Sysmon, Ubuntu, Raspberry Pi, Kali)
- **Sentinel** receives pfSense firewall and DHCP logs and Wazuh alerts, and pushes alerts to Discord

### 🖥️ Compute
- **Home lab server:** MINISFORUM X1 Lite-255 (Ryzen 7 255, 32 GB DDR5) running Ubuntu Server, Docker, Portainer and Uptime Kuma
- **AI server:** Intel i5-13600K + **RTX 4070 12 GB**, 32 GB DDR5, running 24/7 local inference
- **Lab box:** Beelink EQ running Kali Linux, isolated in its own VLAN

---

## 🐧 Open-Source Projects

### 🛡️ [Sentinel: Homelab SOC Dashboard](https://github.com/KevinTechLabs/Homelab-Soc-Dashboard)
A self-hosted SOC dashboard and network threat monitor. The detection engine is standard-library Python: it reads the systemd journal, ufw and pfSense logs, maps every alert to **MITRE ATT&CK**, blocks attackers, and alerts on Discord. Prometheus Alertmanager and GitOps agents can push their alerts in too.

### 🔍 [Homelab SIEM & Detection Lab](https://github.com/KevinTechLabs/Homelab-SIEM-Detection-Lab)
A single-node Wazuh SIEM watching a segmented network. Five custom rules turned **~8,300 false-alarm events** into quiet records, while everything else still alerts at full severity. CIS hardening took the SIEM server from **47 % to 67 %** with zero lockouts.

### 🚀 [Personal CI/CD Platform](https://github.com/KevinTechLabs/Personal-CI-CD)
From `git push` to a running, self-healing service. ruff, bandit, pip-audit and TruffleHog, tests against real Postgres, a Trivy gate, SBOM and **cosign** signing, then pull-based GitOps deploys that roll back automatically on an SLO breach.

### 🗄️ [Desk-Pi-Rack](https://github.com/KevinTechLabs/Desk-Pi-Rack)
The hardware inventory and network design behind everything above: VLAN plan, per-zone firewall rules, forced DNS, IP reputation blocking, intrusion detection, and the lessons learned building it.

### 🎛️ [NexusLab](https://github.com/KevinTechLabs/NexusLab)
A control panel for the homelab. Live metrics, Docker start/stop/logs, Wake-on-LAN, reboot and shutdown for every machine, plus a chat tab backed by local AI, from any browser or as a phone app.

### 🤖 [NexusLLM](https://github.com/KevinTechLabs/NexusLLM)
A private local AI server: Ollama and Open WebUI on an RTX 4070, with local RAG, web search, a phone app, monitoring and Discord alerts, reachable only over Tailscale.

### 🔐 [Stash](https://github.com/KevinTechLabs/Stash-Notes-App)
Encrypted personal notes, kept in two versions on purpose. v1 is a hardened Flask server app; v2 rebuilds it as an installable phone app that encrypts everything on the device with **AES-256-GCM**, works offline and supports recovery codes.

### ☢️ [REACTOR: Hyprland Desktop](https://github.com/KevinTechLabs/Custom-Linux-Waybar)
A nuclear-reactor themed Hyprland setup for Arch / CachyOS: Waybar, a slide-out control-room sidebar, a terminal dashboard and a power menu, installed with one command.

<img src="https://raw.githubusercontent.com/KevinTechLabs/Custom-Linux-Waybar/main/preview.webp" alt="REACTOR Hyprland desktop" width="100%">

---

## 🧰 Toolbox

`pfSense` `Suricata` `pfBlockerNG` `Wazuh` `Sysmon` `Pi-hole` `Docker` `GitHub Actions` `Trivy` `cosign` `Python` `FastAPI` `Flask` `Bash` `Ollama` `Tailscale` `Ubuntu` `Kali` `Arch`

<sub>Every address in my repos is an example. Real IPs, keys and credentials are never published.</sub>
