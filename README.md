# Penetration Testing — Footprinting & Network Scanning

## 📌 Overview

This repository documents my **Week 2 cybersecurity internship activities at Networkwalks**, focusing on two fundamental penetration-testing phases:

1. **Reconnaissance & Footprinting**
2. **Scanning & Network Discovery**

The exercises demonstrated how security professionals can gather publicly available information about an authorized target and identify active hosts within an authorized local network.

The work covered the following Networkwalks modules:

* **W2-PM1 — Multiple Kali Tools**
* **W2-PM3 — Footprinting with Maltego**
* **W2-PM5 — Zenmap Scanning**

The activities were performed against **Networkwalks with secured written permission** and my **own local LAN network**.

---

## ⚠️ Disclaimer

All activities documented in this repository were performed only against systems for which I had authorization or systems that I personally owned.

This project is intended for **educational and research purposes**. Unauthorized scanning, enumeration, or access to systems may be illegal.

---

# 🎯 Objectives

The main objectives of this exercise were to:

* Understand the reconnaissance and footprinting phase of penetration testing.
* Gather publicly available information about a domain.
* Identify technologies used by a web application.
* Resolve domain and DNS information.
* Inspect HTTP response headers.
* Identify the presence of a Web Application Firewall.
* Map relationships and entities using Maltego.
* Identify active hosts on a local network.
* Understand the security implications of information discovered during reconnaissance.

---

# 🛠️ Tools Used

| Tool           | Purpose                                         |
| -------------- | ----------------------------------------------- |
| **Kali Linux** | Operating system used for reconnaissance        |
| **WHOIS**      | Domain registration and name-server information |
| **WhatWeb**    | Web technology fingerprinting                   |
| **Nslookup**   | DNS/domain-to-IP resolution                     |
| **cURL**       | HTTP response-header inspection                 |
| **Wafw00f**    | WAF detection                                   |
| **DNSRecon**   | DNS record enumeration                          |
| **Maltego**    | Relationship and entity mapping                 |
| **Zenmap**     | Network scanning and host discovery             |
| **ip a**       | Local IP/interface identification               |
| **ifconfig**   | Local network interface information             |

The report identifies these tools and their purposes as part of the Week 2 activities.

---

# 🔎 Phase 1 — Footprinting & Reconnaissance

The first phase focused on gathering information about the authorized `networkwalks.com` domain.

## 1. WHOIS

WHOIS was used to obtain domain registration information.

### Why it matters

Registration and DNS information can provide useful background information about a target's infrastructure and hosting environment.

---

## 2. WhatWeb

WhatWeb was used to fingerprint the technologies used by the website.

### Security relevance

Technology and version information can help an attacker determine what software is being used and identify technologies that may require further security review.

The report classified exposed web-technology information as a **Medium-risk finding**.

---

## 3. Nslookup

Nslookup was used to resolve the domain name.

### Security relevance

Knowing the IP address associated with a domain provides information about the network location of the web service.

The report classified this finding as **Low risk**.

---

## 4. cURL

cURL was used to inspect the HTTP response headers.

### Security relevance

HTTP response headers and exposed endpoints can assist with technology fingerprinting and additional enumeration.

This finding was classified as **Low risk**.

---

## 5. Wafw00f

Wafw00f was used to determine whether a Web Application Firewall was protecting the target.

### Security relevance

Identifying defensive technologies can provide information about the security architecture of a web application.

The report classified this finding as **Low risk**.

---

## 6. DNSRecon

DNSRecon was used to enumerate DNS records.


### Security relevance
DNS enumeration is useful during reconnaissance because DNS records can reveal information about how an organization's services and infrastructure are configured.

---

## 7. Maltego

Maltego was used to graphically investigate relationships and entities associated with the domain.

### Findings

The investigation linked the domain to:

* `info@networkwalks.com`
* `abuse@godaddy.com`

### Security relevance

Publicly discoverable email addresses can potentially be abused for phishing, social engineering, or other targeted attacks.

The report classified exposed email targets as **Medium risk**.

---

# 🌐 Phase 2 — Network Scanning & Discovery

The second phase focused on my **own local network**.

## 1. Identifying the Local Network

I first used:

```bash
ip a
```

and:

```bash
ifconfig
```

to identify the local network interface and addressing information.
---

## 2. Zenmap Ping Scan

I used **Zenmap**, the graphical interface for Nmap, to perform a Ping Scan.
A total of **3 live hosts** were identified.

### Security relevance

Internal network discovery can help security teams identify:

* Active devices
* Unexpected systems
* Potentially unauthorized devices
* The general topology of an internal network

The report therefore classified the presence of multiple visible live hosts as a **Medium-risk observation**.

---

# 📊 Risk Analysis

| # | Finding                            | Risk       | Potential Impact                                       |
| - | ---------------------------------- | ---------- | ------------------------------------------------------ |
| 1 | Web technology information exposed | **Medium** | Could help identify software requiring security review |
| 2 | Server IP address identifiable     | **Low**    | Reveals network location of the web service            |
| 3 | HTTP technical information exposed | **Low**    | Can assist fingerprinting and enumeration              |
| 4 | WAF technology identifiable        | **Low**    | Reveals part of the security architecture              |
| 5 | Email targets exposed              | **Medium** | Could support phishing/social engineering              |
| 6 | Multiple live hosts visible        | **Medium** | Unknown devices may potentially exist on a network     |

These findings and their risk classifications are taken directly from the report.

---

# 🛡️ Recommendations

Based on the observations, the following recommendations were identified:

### 1. Review publicly exposed technology information

Organizations should regularly review the amount of information publicly available about their:

* Web technologies
* CMS platforms
* Plugins
* Infrastructure

### 2. Keep software updated

CMS platforms, plugins, and other web technologies should be regularly updated and reviewed against current security advisories.

### 3. Review HTTP headers

HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

### 4. Properly configure and monitor the WAF

The existing **ModSecurity WAF** should remain enabled, properly configured, and monitored.

### 5. Perform regular internal network discovery

Organizations should periodically scan their internal networks to identify active devices and investigate unknown or unauthorized systems.

These recommendations are documented in the original assessment report.

---

# 🧠 Key Lessons Learned

This exercise helped me understand how different reconnaissance tools provide different pieces of information that can be combined to build a picture of a target.

Some of the key lessons were:

* Reconnaissance is an important early stage of penetration testing.
* Different tools provide different types of intelligence.
* DNS information can reveal infrastructure details.
* Web technology fingerprinting can expose useful technical information.
* HTTP headers and public API endpoints can assist enumeration.
* WAF detection can reveal defensive technologies.
* Maltego can help visualize relationships between entities.
* Network scanning can identify active devices within an authorized network.
* Information that appears harmless individually can become more useful when combined.

---

# 🏁 Conclusion

Week 2 provided practical exposure to two foundational penetration-testing activities: **footprinting/reconnaissance and network scanning**.

Using Kali Linux tools including WHOIS, WhatWeb, Nslookup, cURL, Wafw00f, DNSRecon and Maltego, I gathered and analyzed publicly available information about an authorized domain.

I then used Zenmap to perform network discovery on my own local network and identified three live hosts.

Overall, the exercise demonstrated how security professionals can move from **public information gathering to network discovery**, while also assessing the security implications of the information uncovered.

---

## 📚 Project Information

**Program:** Networkwalks Cybersecurity Internship
**Batch:** B083-Networkwalks
**Week:** 2
**Modules:** W2-PM1, W2-PM3, W2-PM5
**Focus:** Footprinting, Reconnaissance & Network Scanning
**Environment:** Kali Linux + Zenmap
**Date:** September 15, 2026
