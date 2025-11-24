# 1️⃣ Introduction

**Tester(s):**  
- Name: Marius Pozo

**Purpose:**  
- Identify vulnerabilities on a basic web application.

**Scope:**  
- Tested components: All page interactions. GET and POST, especially on register. Minor actions on login, reservation, resources and accessed (found) documents.
- Exclusions: None
- Test approach: Gray-box

**Test environment & dates:**  
- Start: 20.11.2025 18:00
- End: 20.11.2025 19:00
- Test environment details: Windows 11, PostGre DB, using Chrome, ZAP and Docker. ZAP: 1 automated scan, 3 active scans. 1h of scans and data review.

**Assumptions & constraints:**  
- We knew there was flaws (most likely): the application system is in development. Working in phases.

---

# 2️⃣ Executive Summary

**Short summary (1-2 sentences):**  Simply ran Docker, composed up the containers making the application online, and ran ZAP on his address. First, an automated scan have been make as a summary. 3 active scans followed to look up for more precise flaws. Stopped at 3 because no more data was added about potential flaws. Also reviewed database PostGre data to see potential flaws manually. Composed down containers after test.

**Overall risk level:** High

**Top 5 immediate actions:**  
1. Path traversal: block URL access without appropriated credential – use an "accept known good" input validation strategy.
2. SQL Injection: check user's inputs, verify request format before processing in DataBase.
3. CSRF: implement anti-CSRF tokens.
4. Content Security Policy (CSP) should be added.
5. Encrypt passwords in PostGre DataBase – good practice to do everywhere.

---

# 3️⃣ Severity scale & definitions

|  **Severity Level**  | **Description**                                                                                                              | **Recommended Action**           |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
|      🔴 **High**     | A serious vulnerability that can lead to full system compromise or data breach (e.g., SQL Injection, Remote Code Execution). | *Immediate fix required*         |
|     🟠 **Medium**    | A significant issue that may require specific conditions or user interaction (e.g., XSS, CSRF).                              | *Fix ASAP*                       |
|      🟡 **Low**      | A minor issue or configuration weakness (e.g., server version disclosure).                                                   | *Fix soon*                       |
| 🔵 **Info** | No direct risk, but useful for system hardening (e.g., missing security headers).                                            | *Monitor and fix in maintenance* |


---

# 4️⃣ Findings

> Fill in one row per finding. Focus on clarity and the most important issues.

| ID | Severity | Finding | Description | Evidence / Proof |
|------|-----------|----------|--------------|------------------|
| F-01 | 🔴 High | SQL Injection | SQL Injection may be possible | `'` character make return of internal error page (500). Boolean manipulation succeeded through custom SQL request. |
| F-02 | 🟠 Medium | anti-CSRF Tokens | No tokens on HTML requests found. Could end up in man-in-the-middle attack.| "No known Anti-CSRF token", said ZAP. |
| F-03 | 🟠 Medium | CSP not set | Content Security Policy (CSP) header not set.  | Header parameter not present |
| F-04 | 🟡 Low | X-Content-Type-Options Header Missing | The Anti-MIME-Sniffing header X-Content-Type-Options was not set to 'nosniff'. Allow older browser version to display the app, and potentially in a way not intended because of older display methods | Header parameter not present |
| F-05 | 🟡 Low | Non-encrypted passwords | Passwords in database are displayed in plain text | Explicit |

---

# 5️⃣ OWASP ZAP Test Report (Attachment)

**https://github.com/Ozenos/CybersecurityCourse/blob/main/BookingSystem-Phase1/zap_report_round1.md**
