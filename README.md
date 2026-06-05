# CertTrace

### Automated SSL Certificate Monitoring & Threat Intelligence Platform


## Overview

CertTrace is an automated threat intelligence platform designed to identify suspicious domains and phishing infrastructure at an early stage by monitoring SSL/TLS Certificate Transparency (CT) logs.

Modern phishing campaigns frequently rely on newly registered domains and valid SSL certificates to appear legitimate. Traditional security solutions often identify these threats only after they become active or are reported by victims. CertTrace addresses this challenge by focusing on **early threat discovery**, enabling analysts to identify potentially malicious infrastructure as it begins to appear on the internet.

The platform combines real-time certificate monitoring, active OSINT hunting, threat scoring, infrastructure enrichment, and analyst dashboards into a unified workflow for cybersecurity research, threat hunting, and proactive security monitoring.

---

## Why CertTrace?

Most security platforms answer:

> "Is this domain already malicious?"

CertTrace attempts to answer:

> "Could this domain become malicious?"

Instead of waiting for domains to be blacklisted, CertTrace monitors newly issued SSL certificates and analyzes suspicious infrastructure before phishing campaigns become widespread.

### Key Differentiators

* Early threat discovery instead of only threat verification
* Real-time Certificate Transparency monitoring
* Active OSINT-based infrastructure hunting
* Automated phishing-focused threat scoring
* Infrastructure enrichment and correlation
* Integrated analyst dashboards
* Centralized IOC management

---

## Features

### Certificate Transparency Monitoring

* Live CertStream integration
* Continuous SSL/TLS certificate monitoring
* Real-time certificate event processing

### Threat Detection Engine

* Brand impersonation detection
* Typosquatting detection
* Homoglyph analysis
* Financial keyword detection
* Suspicious TLD analysis
* Risk-based threat scoring

### Threat Intelligence Enrichment

* DNS Resolution
* WHOIS Intelligence
* TLS Fingerprinting
* IP Intelligence
* AlienVault OTX Integration
* Shodan Integration

### Investigation & Analytics

* IOC Management
* Investigation Reports
* Infrastructure Analysis
* Threat Topology Visualization
* Risk Categorization
* Analyst Notes & Verdicts

### Dashboards

* FastAPI Monitoring Dashboard
* Streamlit Analytics Dashboard
* Real-Time WebSocket Updates
* Threat Statistics & Metrics

---

## System Architecture

```text
                    Certificate Transparency Logs
                                │
                                ▼
                       CertStream Ingestor
                                │
                                ▼
                          Async Queue
                                │
                   ┌────────────┴────────────┐
                   │      Worker Pool        │
                   └────────────┬────────────┘
                                │
          ┌─────────────────────┼─────────────────────┐
          ▼                     ▼                     ▼
   Threat Scoring       Brand Hunting          Allowlist
      Engine              Module              Filtering
          │
          ▼
  Intelligence Enrichment
(DNS • WHOIS • TLS • OTX • Shodan)
          │
          ▼
      IOC Database
          │
    ┌─────┴─────┐
    ▼           ▼
 FastAPI     Streamlit
 Dashboard   Dashboard
```

---

## Project Structure

```text
CERTTRACE/
│
├── certtrace/
│   ├── ingestor.py
│   ├── hunter.py
│   ├── worker.py
│   ├── scorer.py
│   ├── enricher.py
│   ├── database.py
│   ├── allowlist.py
│   ├── reporter.py
│   ├── investigator.py
│   ├── whois_lookup.py
│   ├── shodan_lookup.py
│   └── otx_lookup.py
│
├── static/
│   ├── index.html
│   ├── app.js
│   └── style.css
│
├── data/
│   ├── certtrace.db
│   └── tranco_top1m.csv
│
├── logs/
│   └── certtrace.log
│
├── main.py
├── api.py
├── dashboard.py
├── config.py
├── check_db.py
├── requirements.txt
├── protected_targets.txt
├── README.md
└── PRODUCTION.md
```

---

## Technology Stack

### Backend

* Python
* FastAPI
* AsyncIO
* Uvicorn
* WebSockets

### Threat Intelligence

* CertStream
* AlienVault OTX
* Shodan
* WHOIS
* DNS Intelligence

### Database

* SQLite

### Frontend & Analytics

* Streamlit
* HTML
* CSS
* JavaScript

### Data Processing

* Pandas
* TLDExtract
* Python-WHOIS
* dnspython

---

## Installation

### Clone Repository

```bash
git clone https://github.com/yourusername/certtrace.git
cd certtrace
```

### Create Virtual Environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

#### Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Configuration

### Optional Environment Variables

```bash
SHODAN_API_KEY=your_shodan_api_key
OTX_API_KEY=your_otx_api_key
```

### Protected Targets

Add organizations or brands to:

```text
protected_targets.txt
```

Example:

```text
sbi
hdfc
icici
paypal
amazon
microsoft
google
```

---

## Running CertTrace

### Start Complete Platform

```bash
python main.py
```

### Start FastAPI Backend

```bash
uvicorn api:app --reload
```

### Start Streamlit Dashboard

```bash
streamlit run dashboard.py
```

### Database Statistics

```bash
python check_db.py
```

---

## Threat Detection Workflow

```text
Certificate Event
        │
        ▼
 Domain Extraction
        │
        ▼
 Domain Analysis
        │
        ▼
 Threat Scoring
        │
        ▼
 Intelligence Enrichment
        │
        ▼
 IOC Creation
        │
        ▼
 Database Storage
        │
        ▼
 Dashboard Visualization
```

---

## Threat Scoring Methodology

CertTrace evaluates domains using multiple heuristic indicators:

| Indicator                   | Description                         |
| --------------------------- | ----------------------------------- |
| Brand Similarity            | Detects impersonation attempts      |
| Typosquatting               | Identifies spelling variations      |
| Homoglyph Analysis          | Detects visually similar characters |
| Financial Keywords          | Banking & payment related terms     |
| High-Risk TLDs              | Suspicious domain extensions        |
| Domain Structure            | Abnormal naming patterns            |
| Certificate Characteristics | SSL/TLS metadata analysis           |

Domains are classified into:

| Score    | Risk Level |
| -------- | ---------- |
| 0 – 30   | Low        |
| 31 – 60  | Medium     |
| 61 – 80  | High       |
| 81 – 100 | Critical   |

---

## Dashboard Features

### Real-Time Monitoring

* Live IOC Feed
* Threat Scores
* Connection Status
* Recent Discoveries

### Analytics

* IOC Distribution
* Threat Trends
* Certificate Authority Analysis
* Detection Statistics

### Investigation

* Domain Lookup
* Infrastructure Analysis
* WHOIS Information
* DNS Records
* Threat Intelligence Correlation

---

## Example Use Cases

### SOC Operations

Monitor emerging phishing infrastructure before attacks become active.

### Threat Hunting

Identify suspicious domains targeting organizations or industries.

### Cybercrime Research

Analyze infrastructure used in phishing and impersonation campaigns.

### Security Awareness

Study trends in domain abuse and certificate misuse.

---

## Future Enhancements

* Machine Learning-Based Detection
* SIEM Integration (Wazuh, Splunk, ELK)
* Docker Deployment
* PostgreSQL Migration
* Multi-User Authentication
* Automated Alerting
* Cloud Deployment
* MISP Integration
* STIX/TAXII Support
* Threat Correlation Engine

---

## Disclaimer

CertTrace is intended for educational, research, and defensive cybersecurity purposes only. The platform is designed to support threat intelligence gathering, infrastructure analysis, and proactive security monitoring. Users are responsible for ensuring compliance with applicable laws, regulations, and organizational policies.

---

Cybersecurity Student | Threat Intelligence Enthusiast | OSINT Researcher

If you find this project useful, consider giving it a ⭐ on GitHub.
