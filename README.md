# 🛡️ Operation Swift Recovery
### Cybersecurity Incident Analysis — GlobalTrust Bank | March 15, 2024

> A multi-vector cyber attack hit GlobalTrust Bank at 02:00 UTC. 550 attackers. 13 countries. 3 hours. $890K in damage. This project is a full forensic data analysis of what happened, who did it, and how to prevent it from happening again.

---

## 📌 The Scenario

On March 15, 2024, GlobalTrust Bank suffered a coordinated cyber attack involving five simultaneous attack vectors: DDoS SYN Flood, DDoS UDP Flood, SQL Injection, Brute Force, and XSS. The attack lasted 3 hours, generated 15,500 attack events from 550 unique IPs across 13 countries, and caused $890,000 in direct losses while affecting 340,000 customers.

The central question driving this analysis: **Was this a planned, coordinated attack — or random internet noise?**

---

## 📊 What This Analysis Covers

The notebook is structured around **15 analysis questions** across 5 parts:

| Part | Focus | Questions |
|------|-------|-----------|
| A | Understanding the Attack | Coordination proof, frequency vs. danger, peak timing |
| B | Geographic Attribution | Country origin, anonymization tools, state-sponsored indicators |
| C | Threat Actor Analysis | IP danger scoring, campaign classification, ISP tiering |
| D | Business Recommendations | Service restoration priority, IP blocking criteria, security investments |
| E | Deliverables | Executive dashboard, board summary, CISO technical report |

---

## 🔑 Key Findings

- ✅ **Coordinated attack confirmed** — all 5 vectors launched within 27.8 seconds of each other
- ✅ **74.9%** of attacker IPs used all 5 attack types simultaneously
- ✅ **SQL Injection** was 19× more dangerous than DDoS by weighted danger score — with a 24.2% WAF bypass rate
- ✅ **Peak at 02:58 UTC** — deliberately timed to exploit minimum overnight SOC staffing
- ✅ **55%** of attackers used anonymization tools (TOR, VPN, or Proxy) — computed via set union to avoid double-counting
- ✅ **77 APT-suspected IPs** generated 15% of all attack traffic
- ✅ **No data stolen. Zero accounts compromised.** MFA held 100%.
- ✅ A **$575K security investment** plan reduces repeat-attack risk from 40% → under 10%

---

## 🗄️ Data

The analysis runs against a **MySQL database** (`globaltrust_incident`) with 4 tables:

| Table | Rows | Description |
|-------|------|-------------|
| `attack_logs` | 15,500 | Every attack event with timestamp, IP, type, severity, blocked status |
| `ip_intelligence` | 550 | Geolocation, ISP, threat score, anonymization flags per attacker IP |
| `affected_services` | 10 | Bank's internal services with criticality ratings |
| `incident_timeline` | 21 | SOC response log |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python 3 | Core analysis language |
| Pandas | Data manipulation and enrichment |
| NumPy | Numerical operations |
| Matplotlib / Seaborn | Visualizations |
| SQLAlchemy | MySQL database connection |
| MySQL | Attack data storage |
| python-dotenv | Secure credential management |
| Jupyter Notebook | Analysis environment |

---

## 🚀 How to Run It

**1. Clone the repo**
```bash
git clone https://github.com/YOUR_USERNAME/operation-swift-recovery.git
cd operation-swift-recovery
```

**2. Install dependencies**
```bash
pip install pandas numpy matplotlib seaborn sqlalchemy mysql-connector-python python-dotenv
```

**3. Set up your environment variables**

Copy `.env.example` to `.env` and fill in your MySQL credentials:
```bash
cp .env.example .env
```

```
DB_USER=your_mysql_username
DB_PASSWORD=your_mysql_password
DB_HOST=127.0.0.1
DB_NAME=globaltrust_incident
```

**4. Set up the database**

Restore the `globaltrust_incident` MySQL database, then open the notebook:
```bash
jupyter notebook notebook/operation_swift_recovery.ipynb
```

---

## 📁 Repository Structure

```
operation-swift-recovery/
├── README.md
├── .env.example
├── notebook/
│   └── operation_swift_recovery.ipynb
└── presentation/
    └── cyberstorm_presentation.pdf
```

---

## 👥 Team

| Name | Role |
|------|------|
| Saleh Hossam | Lead Analyst — coordination proof, timing analysis, danger scoring, CISO report |
| Toka Gbr | Geographic attribution, anonymization analysis |
| Jana Mohamed | Threat actor profiling, ISP tiering |
| Nour Gomaa | Business recommendations, service restoration |
| Toka Mohamed | Executive dashboard, board summary |

---

## 🏫 Program

This project was completed as part of the **DEBI Business Analytics Program** — Bnaah Masr el Raqameya (بناة مصر الرقمية).

---

## ⚠️ Disclaimer

This is a **simulated dataset** created for educational purposes. GlobalTrust Bank is a fictional organization. All IP addresses, attack data, and financial figures are synthetic.
