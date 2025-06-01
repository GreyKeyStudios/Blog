
---
title: "Automated Threat Intelligence with Python"
date: 2025-05-02
categories: [Cybersecurity, Threat Intelligence]
tags: [python, APIs, threat-data, security-automation]
---

# 🕵🏾‍♂️ Threat Intel Project: Building an Automated Threat Feed Harvester

**Part of the Cybersecurity Projects series.**  
In this post, I’ll break down how I built a Python-based automation tool to collect and log threat intelligence from multiple sources — specifically, VirusTotal, AlienVault OTX, and AbuseIPDB.

The goal was simple:  
🎯 Build a script that could pull data from real-world threat feeds and save it locally for analysis or future use.

---

## 🧠 Why Threat Intelligence?

Threat intelligence is a critical pillar in cybersecurity. It’s what gives SOC teams the edge — knowing what IPs, hashes, or domains are up to no good *before* they reach your network. While there are expensive commercial solutions, most of these sources offer public APIs, and with a little Python, we can tap directly into them ourselves.

This project helped me learn:
- How to work with REST APIs
- How to safely handle and log sensitive data
- How to automate data collection from multiple threat sources

---

## 🛠️ Tools & Data Sources

Here are the threat intel feeds I integrated:

- 🔬 **VirusTotal**: File hash and domain reputation service.
- 🛰️ **AlienVault OTX**: Community-powered threat indicators (IOCs).
- 🛡️ **AbuseIPDB**: A growing blacklist of malicious IPs based on community reports.

All of these platforms offer free API access with usage limits.

---

## 🧪 How It Works

### 1. 📁 Project Structure

```bash
Threat-Intelligence/
├── src/
│   ├── vt_query.py        # VirusTotal logic
│   ├── otx_query.py       # AlienVault logic
│   ├── abuseipdb_query.py # AbuseIPDB logic
│   └── main.py            # Orchestrates the full run
├── .env.example           # API key template
├── requirements.txt       # Python deps (requests, python-dotenv, etc.)
├── README.md              # Project documentation
```

### 2. 🔑 Secure API Access

To avoid hardcoding sensitive keys, I used a `.env` file (ignored by Git). Here's what the template looks like:

```env
VT_API_KEY=your_virustotal_key
OTX_API_KEY=your_otx_key
ABUSEIPDB_API_KEY=your_abuseipdb_key
```

### 3. 📦 Output

Each module stores results in:
- `results/virustotal.json`
- `results/otx.json`
- `results/abuseipdb.json`

There’s also support for saving in CSV format for those who prefer Excel-style review.

---

## 📸 Screenshots (Coming Soon)

I’ll be adding screenshots of:

- API responses in JSON format
- Terminal output after running the main script
- Sample results in Excel

---

## 🧩 Lessons Learned

- Some APIs rate-limit hard. Solution: rotate queries or introduce `time.sleep()`.
- OTX gives a lot of raw data — parsing and extracting useful fields was key.
- I used logging instead of `print()` to track runs and errors in production-style output.

---

## 🚀 Future Enhancements

- Add Shodan or URLScan as additional sources
- Convert it into a CLI tool with argument parsing
- Build a basic dashboard to visualize results using Flask or Streamlit
- Schedule as a daily cron job for passive data collection

---

## 📎 Repo Link

All code and instructions are in the GitHub repo:  
[https://github.com/GreyKeyStudios/CyberSecurity-Projects/tree/main/Threat-Intelligence](https://github.com/GreyKeyStudios/CyberSecurity-Projects/tree/main/Threat-Intelligence)
