# 📱 PhoneGuard Enterprise API

[![Uptime](https://img.shields.io/badge/Uptime-99.99%25-brightgreen.svg)](https://phoneguard-api.onrender.com/health)
[![Latency](https://img.shields.io/badge/Latency-sub--5ms-blue.svg)](https://phoneguard-api.onrender.com)
[![Python](https://img.shields.io/badge/Python-3.11%2B-blue.svg)](https://www.python.org/)
[![RapidAPI](https://img.shields.io/badge/RapidAPI-Marketplace%20Ready-orange.svg)](https://rapidapi.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **Global Phone Number Validation, E.164 Normalization, Carrier Resolution & VoIP Fraud Shield.**  
> High-performance alternative to Twilio Lookup and Numverify. Sub-5ms local evaluation covering 200+ countries.

---

## 🚀 Overview

**PhoneGuard Enterprise** verifies and enriches international phone numbers in real time. It normalizes numbers to international standard **E.164 format**, identifies carrier networks, distinguishes Mobile from Landline and high-risk Virtual **VoIP numbers** (Google Voice, TextNow, Bandwidth.com), and calculates an automated 0–100 fraud risk score.

---

## ⚡ Key Capabilities

- 🌍 **200+ Country Support:** Validates national format, international dial codes, and ISO country codes.
- 📱 **Line-Type Intelligence:** Classifies numbers into `MOBILE`, `LANDLINE`, `VOIP`, `TOLL_FREE`, or `PAGER`.
- 🛡️ **VoIP & Fraud Shield:** Automatically flags and blocks virtual disposable burner numbers used in SMS OTP abuse.
- 🏢 **Carrier Detection:** Resolves primary telecom carriers (AT&T, Verizon, T-Mobile, Vodafone, BT, Jio, Airtel).
- ⚡ **Ultra-Low Latency:** Evaluates numbers locally in sub-5ms with zero third-party API dependencies.

---

## 📡 Live Production Endpoints

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/v1/lookup?phone=+14155552671` | Verify format, carrier, line-type, and fraud score. |
| `POST` | `/v1/lookup` | JSON payload verification: `{"phone": "+447911123456"}`. |
| `GET` | `/health` | Health and uptime monitoring probe. |

---

## 💻 Quick Start & Code Examples

### 1. cURL
```bash
curl -X GET "https://phoneguard-api.onrender.com/v1/lookup?phone=%2B14155552671" \
     -H "Accept: application/json"
```

### 2. Python (`requests`)
```python
import requests

url = "https://phoneguard-api.onrender.com/v1/lookup"
params = {"phone": "+44 7911 123456"}

response = requests.get(url, params=params)
data = response.json()

print(f"E.164:      {data['e164']}")
print(f"Country:    {data['country']['name']}")
print(f"Line Type:  {data['line_type']}")
print(f"Carrier:    {data['carrier']}")
print(f"Fraud Risk: {data['fraud_risk_score']}/100 ({data['recommendation']})")
```

---

## 📦 JSON Response Schema

```json
{
  "valid": true,
  "raw_input": "+1 (415) 555-2671",
  "e164": "+14155552671",
  "country": {
    "name": "United States / Canada",
    "iso2": "US",
    "iso3": "USA",
    "dial_code": "+1"
  },
  "line_type": "MOBILE",
  "carrier": "North American Numbering Plan (NANPA)",
  "fraud_risk_score": 10,
  "recommendation": "ALLOW",
  "is_voip": false,
  "processing_time_ms": 0.08
}
```

---

## 💰 RapidAPI Pricing Tiers

| Plan | Monthly Fee | Included Quota | Overages | Target Audience |
| :--- | :--- | :--- | :--- | :--- |
| **Free** | `$0.00 / mo` | 100 requests | Rate-limited | Testing & Developers |
| **Basic** | `$9.99 / mo` | 3,000 requests | `$0.004 / req` | Indie Apps & SMS Verification |
| **Pro** | `$29.99 / mo` | 12,000 requests | `$0.002 / req` | SaaS Platforms & Anti-Spam |
| **Ultra**| `$79.99 / mo` | 50,000 requests | `$0.001 / req` | High-Volume Telephony |

---

## 👨‍💻 Maintainer & Engineering Contact
- **Architecture Lead:** **Liam Vance** — Director of Cloud & API Operations
- **Organization:** VIBE NOW Technologies
- **Inquiries:** `liamvance.dev@gmail.com`
