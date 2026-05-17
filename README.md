# IntruSense v2.0
### Intelligent Deception & Attacker Intelligence Platform

> *"We don't just detect attacks. We let attackers walk into our traps, profile them, and expose every move they make."*

---

## 🚀 Quick Start

```bash
git clone https://github.com/your-org/intrusense.git
cd intrusense
cp backend/.env.example backend/.env
docker-compose up --build
```

Open **http://localhost:5173** for the live dashboard.

| Service | URL | Description |
|---|---|---|
| Dashboard | http://localhost:5173 | Live threat monitoring UI |
| API | http://localhost:3000 | REST + Socket.io backend |
| HTTP Honeypot | http://localhost:8080 | Fake login/admin pages |
| SSH Honeypot | localhost:2222 | Fake SSH server |
| FTP Honeypot | localhost:2121 | Fake FTP server |

---

## 🧠 What is IntruSense?

IntruSense is a **deception-based cybersecurity platform** that silently traps attackers, profiles them in real time, and explains what they're doing in plain English.

Instead of just blocking threats, IntruSense:

- **Deploys honeypots** — fake login pages, SSH/FTP servers, and canary files that lure attackers
- **Profiles every attacker** — geo-location, device fingerprinting, attack classification, and threat scoring
- **Summarizes attacks with AI** — plain-English explanations for non-technical stakeholders
- **Shows smart notifications** — grouped by IP and type, no alert flooding
- **Maps attacks in real time** — including local LAN attackers plotted geographically

---

## 📁 Project Structure

```
intrusense/
├── backend/                    # Node.js API + Honeypot Engine
│   ├── server.js               # Main server (API + all honeypots)
│   ├── database.js             # SQLite database layer
│   ├── alert-engine.js         # Smart alert grouping + AI summaries
│   ├── capture-pipeline.js     # IP enrichment + attack classification
│   ├── ai-summary.js           # AI-powered attack explanation
│   ├── honeypot-pages.js       # Fake HTML pages served to attackers
│   ├── demo-seed.js            # Demo data seeder for presentations
│   ├── Dockerfile
│   └── package.json
│
├── frontend/                   # React Dashboard
│   ├── src/
│   │   ├── components/
│   │   │   ├── Landing.jsx     # Landing page
│   │   │   └── Dashboard.jsx   # Live dashboard with attack map
│   │   └── hooks/
│   │       └── useSocket.js    # Real-time Socket.io hook
│   ├── nginx.conf              # Production nginx config
│   ├── Dockerfile
│   └── package.json
│
├── attacker-sim/               # Attack simulation scripts (for testing)
│   ├── 01_recon_portscan.sh
│   ├── 02_web_fuzzing.sh
│   ├── 03_sqli_probe.sh
│   ├── 04_xss_probe.sh
│   ├── 05_brute_force_ssh.sh
│   ├── 06_credential_stuffing.sh
│   ├── 07_canary_trap.sh
│   ├── 08_slow_recon.sh
│   └── run_all_attacks.sh
│
├── docs/                       # Documentation
│   ├── ARCHITECTURE.md
│   
│
└── docker-compose.yml          # One-command deployment
```

---

## ⚙️ Environment Variables

Create a `.env` file inside the `backend/` folder:

```env
PORT=3000
HTTP_HONEYPOT_PORT=8080
SSH_HONEYPOT_PORT=2222
FTP_HONEYPOT_PORT=2121
DEMO_MODE=true          # Seeds the database with realistic sample data
```

---

## 🎯 Demo Mode

Set `DEMO_MODE=true` to auto-seed realistic attack data — perfect for demos and presentations.

The dashboard will show:
- 5 curated attacks from different countries
- Port scans, brute force, SQL injection, canary trap triggers
- AI-generated summaries explaining each attack in plain English

---

## 🔒 Security Architecture

IntruSense uses **isolated honeypot architecture**:

- Honeypots run on separate ports from the main API
- All honeypot data is read-only to the dashboard
- No actual system access is ever granted to attackers
- Captured credentials are stored locally for forensic analysis

---

## 📊 Tech Stack

| Layer | Technology |
|---|---|
| Backend | Node.js, Express, Socket.io |
| Database | SQLite (better-sqlite3) |
| IP Intelligence | geoip-lite, ip-api.com |
| Frontend | React 18, Vite |
| Maps | Leaflet.js |
| Containerization | Docker, Docker Compose |
| Honeypots | Raw TCP (SSH/FTP), HTTP |

---

## 🧪 Simulating Attacks (Testing)

Use the included attacker simulation scripts to test the platform locally:

```bash
cd attacker-sim
chmod +x run_all_attacks.sh
./run_all_attacks.sh
```

> ⚠️ Run these only against your own local instance. Never use against external systems.

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.
