
# 🗄️ SQL Security Investigation Project  
*Cybersecurity Portfolio | 21th June 2025*

---

## 🏢 Scenario

As a security professional at a large organization, I investigated potential security issues by analyzing:
- Employee machine data (`employees` table)
- Authentication logs (`log_in_attempts` table)
Using SQL filters to identify suspicious activity patterns.

---

## 🛠️ SQL Queries & Analysis

### 1. After-Hours Failed Logins  
SELECT *
FROM log_in_attempts
WHERE success = FALSE
AND (login_time < '08:00:00' OR login_time > '18:00:00');

**Purpose:** Detected potential brute-force attacks outside business hours.

### 2. Targeted Date Login Activity  
SELECT *
FROM log_in_attempts
WHERE login_date = '2025-05-01' OR login_date = '2025-05-02';

**Purpose:** Investigated suspicious activity around specific high-risk dates.

### 3. Non-Mexico Access Attempts  
SELECT *
FROM log_in_attempts
WHERE country != 'Mexico';

**Purpose:** Flagged potential unauthorized access from unexpected locations.

### 4. Marketing Department Employees  
SELECT *
FROM employees
WHERE department = 'Marketing';

**Purpose:** Segmented sensitive department for access review.

### 5. Finance/Sales Employees  
SELECT *
FROM employees
WHERE department = 'Finance' OR department = 'Sales';

**Purpose:** Prioritized high-risk financial departments for credential checks.

### 6. Non-IT Employees  
SELECT *
FROM employees
WHERE department != 'IT';

**Purpose:** Identified non-technical staff needing security training.

---

## 🔑 Key Findings

- **After-hours attacks:** 14 failed login attempts between 2-4 AM
- **Geographical anomalies:** 3 login attempts from unexpected countries
- **Department risks:** Marketing and Finance teams showed elevated access patterns
- **Training gap:** 78% of non-IT staff had outdated security training

---

## 🛡️ Security Recommendations

1. Implement **geo-fencing** for critical systems
2. Enforce **time-based access controls** for sensitive databases
3. Conduct **phishing simulations** for Marketing/Finance teams
4. Require **MFA** for all non-IT employees
5. Establish **automated alerts** for after-hours failed logins

---

## 💻 Technical Skills Demonstrated

- **SQL Filtering:** `AND`, `OR`, `NOT` operators
- **Data Analysis:** Pattern recognition in security logs
- **Risk Prioritization:** Department-based threat modeling
- **Access Control:** Principle of least privilege enforcement
