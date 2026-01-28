# SOC Dashboard – SSH Brute Force Detection

## 🎯 Objective
Provide SOC analysts with real-time visibility into SSH brute force activity targeting Linux systems.

---

## 📊 Dashboard Panels

### 1️⃣ Failed SSH Logins Over Time
- **Data Source:** /var/log/auth.log
- **Metric:** Count of "Failed password" events
- **Visualization:** Time series
- **Purpose:** Identify attack bursts and brute force attempts

---

### 2️⃣ Top Source IPs by Failed Logins
- **Metric:** Number of failed SSH attempts per IP
- **Visualization:** Bar chart
- **Use Case:** Identify attacking IP addresses

---

### 3️⃣ Invalid User Attempts
- **Metric:** Failed logins for non-existent users
- **Field:** "invalid user"
- **Purpose:** Detect automated attacks and scanning activity

---

### 4️⃣ SSH Login Success vs Failure Ratio
- **Metric:** Accepted password vs Failed password
- **Visualization:** Pie chart
- **Purpose:** Spot suspicious successful logins following brute force

---

## 🚨 Alerts & Thresholds

### SSH Brute Force Alert
IF failed_ssh_logins > 5
FROM same_ip
WITHIN 5 minutes
THEN trigger alert "SSH Brute Force Detected"


---

## 🛡️ SOC Analyst Actions
- Investigate source IP reputation
- Correlate with successful login events
- Escalate if valid account compromise is suspected
- Apply blocking or rate-limiting controls

---

## 🧠 Mapped MITRE ATT&CK
- **T1110 – Brute Force**
- **T1110.001 – Password Guessing**

---

## ✅ Outcome
This dashboard enables early detection of brute force attacks and supports rapid response to prevent account compromise.

