

# 🛡️ Cyber Security Intern Task 2

## Security Log Analysis & Threat Detection using Elasticsearch & Kibana

---

**Tester Name:** Newaz Nezif
**Role:** Cybersecurity Intern
**Date:** December 18, 2025

---

## 📌 Overview

This project documents a **security log analysis and threat detection exercise** performed using **Elasticsearch** and **Kibana**.

The objective was to analyze centralized security logs stored in the `soclog` index to identify suspicious activity, correlate events, and simulate real-world **SOC (Security Operations Center)** monitoring workflows.

---

## ⚙️ Environment Setup & Logging Workflow

### 1️⃣ System Environment

* Analysis conducted on a **local machine**
* All services hosted locally
* Dedicated Elasticsearch index: `soclog`
* Environment isolated from production systems

---

### 2️⃣ Data Sources & Log Collection

Security-relevant logs ingested into Elasticsearch included:

* Authentication attempts
* Malware detections
* File access events
* Network connection attempts

**Normalized Fields:**

* `@timestamp`
* `action`
* `ip`
* `threat`
* `user`

This normalization enabled efficient querying, filtering, and correlation.

---

### 3️⃣ Tools Used

| Tool                   | Purpose                                  |
| ---------------------- | ---------------------------------------- |
| Elasticsearch          | Log storage, indexing, and search        |
| Kibana                 | Visualization and query analysis         |
| Kibana Data Visualizer | Field distribution and behavior analysis |

---

### 4️⃣ Querying & Filtering

Custom Elasticsearch queries were written to detect:

* Failed login attempts
* Malware detections (Trojan, Rootkit, Ransomware)
* Suspicious IP-based activity
* Combined high-risk security events

---

### 5️⃣ Analysis Workflow

* Log exploration using **Discover** panel in Kibana
* Identification of suspicious users, IPs, and threats
* Sorting and filtering by `@timestamp`
* Screenshot capture for reporting and evidence

---

### 6️⃣ Monitoring & Threat Detection

* Failed logins monitored for brute-force or credential stuffing
* Malware detections correlated by user and IP
* Connection and file access events analyzed for anomalies

---

## 📊 Elasticsearch Dashboard Overview

The dashboard provides a consolidated view of:

* Authentication activity
* Malware detections
* File access
* Connection attempts

Key fields (`@timestamp`, `action`, `ip`, `threat`, `user`) enable rapid identification of anomalies and prioritization of security incidents.

---

## 🚨 Section 1: Failed Login Attempt Detection

**Query Used**

```text
action: "login failed"
```

**Description**
Identifies failed authentication attempts that may indicate unauthorized access attempts.

**Findings**

* Multiple failed logins from different IP addresses
* Several users targeted within a short time window

**Severity:** Medium

**SOC Assessment**
Failed logins are early indicators of compromise and require monitoring to detect brute-force activity.

---

## 🦠 Section 2: Malware Detection Events

**Query Used**

```text
action: "malware detected"
```

**Description**
Detects malware activity including Trojans, Rootkits, Worms, and Ransomware behavior.

**Findings**

* Repeated Trojan detections
* Presence of high-impact threats (Rootkit & Ransomware indicators)

**Severity:** High

**SOC Assessment**
Malware detections represent confirmed security incidents requiring immediate response.

---

## 🐴 Section 3: Trojan Malware Detection

**Query Used**

```text
action: "malware detected" AND threat: "Trojan Detected"
```

**Findings**

* Multiple users and IPs affected
* Indicators of potential lateral movement

**Affected Users**

* alice, bob, charlie, david, eve

**Affected IPs**

* 10.0.0.5
* 172.16.0.3
* 192.168.1.101
* 203.0.113.77

**Severity:** High

**SOC Assessment**
Trojan activity confirms system compromise and requires endpoint isolation and remediation.

---

## 🌐 Section 4: IP-Based Activity Correlation

**Query Used**

```text
ip : "10.0.0.5" OR ip : "172.16.0.3" OR ip : "192.168.1.101" OR ip : "198.51.100.42" OR ip : "203.0.113.77"
```

**Findings**

* External IPs associated with authentication and file access
* Internal IPs linked to malware and ransomware behavior
* Multiple event types from the same IPs

**Severity:** High

**Security Impact**
Correlation suggests attack progression rather than isolated events.

---

## 🔥 Section 5: High-Risk Event Aggregation

**Query Used**

```text
action : "malware detected" OR action : "connection attempt" OR action : "login failed"
```

**Findings**

* Malware + failed logins + repeated connection attempts
* Converging activity across internal and external IPs

**Severity:** High

**Security Impact**
Helps detect multi-stage attacks (initial access → execution → persistence).

---

## 📈 Field Analysis

### 🔹 Field: `ip`

| IP Address    | Observation                             |
| ------------- | --------------------------------------- |
| 203.0.113.77  | Frequent failed logins & recon activity |
| 172.16.0.3    | Internal malware & ransomware behavior  |
| 10.0.0.5      | Rootkit-related detections              |
| 198.51.100.42 | Suspicious external activity            |
| 192.168.1.101 | Repeated connection attempts            |

**Insight:** Mixed internal and external threats indicate both intrusion and internal compromise.

---

### 🔹 Field: `action`

* Connection attempts (24%)
* File accessed (22%)
* Login success (22%)
* Malware detected (22%)
* Login failed (10%)

**Insight:** Presence of malware alongside access events suggests attack chaining.

---

### 🔹 Field: `threat`

* Trojan Detected (54.5%)
* Rootkit Signature (18.2%)
* Ransomware Behavior (9.1%)
* Spyware Alert (9.1%)
* Worm Infection Attempt (9.1%)

**Insight:** Multi-stage advanced threat activity detected.

---

### 🔹 Field: `user`

* bob (28%)
* david (24%)
* charlie (18%)
* alice (16%)
* eve (14%)

**Insight:** Multiple user accounts potentially compromised or targeted.

---

## 🏁 Conclusion

This exercise demonstrated practical **SOC-level log analysis** and **threat detection** using Elasticsearch and Kibana. The findings highlight the importance of:

* Centralized logging
* Event correlation
* Monitoring authentication failures
* Rapid identification of malware indicators

The convergence of malware detections, failed logins, and suspicious IP activity suggests realistic attack scenarios involving initial access, persistence, and lateral movement.

This task strengthened hands-on skills in:

* Log analysis
* Threat correlation
* Security monitoring
* Incident prioritization

---

## 🙌 Acknowledgment

This project was conducted strictly for **educational and training purposes** in a controlled environment.

---

## 🚀 Next Steps (Optional Enhancements)

* Add Kibana dashboard screenshots
* Create alerting rules
* Integrate detection with SIEM workflows
* Expand correlation with timelines

---

### ✅ NEXT ACTION

1. Save this as **`README.md`**
2. In VS Code terminal:

```bash
git add README.md
git commit -m "Add Cyber Security Intern Task 2 log analysis report"
git push
```


