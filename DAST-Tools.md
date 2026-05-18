# 🌐 Dynamic Application Security Testing (DAST)

## 📌 DAST คืออะไร?

**DAST (Dynamic Application Security Testing)** คือกระบวนการตรวจสอบความปลอดภัยของแอปพลิเคชันในขณะที่ระบบกำลังทำงานอยู่ (Runtime)

ต่างจาก SAST ที่ตรวจ Source Code โดย DAST จะทำการจำลองการโจมตีจากภายนอกผ่าน:

- HTTP / HTTPS Requests
- API Requests
- Web Forms
- Authentication Flows
- File Upload
- Session Management

DAST สามารถช่วยค้นหาช่องโหว่ที่เกิดขึ้นจริงในระบบขณะทำงานได้

---

## 🎯 ตัวอย่างช่องโหว่ที่ DAST สามารถตรวจพบได้

| ประเภทช่องโหว่             | รายละเอียด                             |
| -------------------------- | -------------------------------------- |
| SQL Injection              | การแทรกคำสั่ง SQL ผ่าน Input           |
| Cross-Site Scripting (XSS) | การ Inject Script เข้า Web Application |
| Command Injection          | การ Execute Command ผ่าน User Input    |
| Directory Traversal        | การเข้าถึงไฟล์นอก Path ที่กำหนด        |
| Broken Authentication      | ปัญหาด้าน Login / Session              |
| SSL/TLS Misconfiguration   | การตั้งค่าการเข้ารหัสที่ไม่ปลอดภัย     |
| Exposed Admin Panel        | การเปิดเผยหน้าจัดการระบบ               |

---

# 🛠 เครื่องมือ DAST และ Web Security Tools

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">1. CMSeeK</span></summary>

## 📖 ภาพรวม

CMSeeK เป็นเครื่องมือสำหรับตรวจสอบ:

> **CMS Detection and Enumeration**

ใช้ค้นหา Content Management System ที่เว็บไซต์ใช้งานอยู่ เช่น:

- WordPress
- Joomla
- Drupal

---

## 🔍 สามารถตรวจพบ

- CMS Type
- CMS Version
- Installed Plugins
- Themes
- Known Vulnerabilities

---

## ✅ จุดแข็ง

- ระบุ CMS ได้แม่นยำ
- ใช้งานง่าย
- Scan ได้รวดเร็ว

## ⚠️ ข้อจำกัด

- เน้นเฉพาะ CMS

## 🎯 เหมาะสำหรับ

- CMS Security Assessment
- Web Enumeration

</details>

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">2. Nikto</span></summary>

## 📖 ภาพรวม

Nikto เป็น Web Server Vulnerability Scanner

ใช้ตรวจสอบ:

- Web Server Misconfiguration
- Dangerous Files
- Default Pages
- Outdated Components

---

## 🔍 สามารถตรวจพบ

- Default Credentials
- Directory Listing
- Server Information Disclosure
- Known Vulnerabilities

---

## ✅ จุดแข็ง

- ใช้งานง่าย
- Database ช่องโหว่เยอะ

## ⚠️ ข้อจำกัด

- Noise สูง
- อาจถูก IDS/IPS ตรวจจับง่าย

## 🎯 เหมาะสำหรับ

- Initial Web Assessment
- Web Server Audit

</details>

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">3. Nmap</span></summary>

## 📖 ภาพรวม

Nmap เป็นเครื่องมือสำหรับ:

> **Network Discovery + Service Enumeration**

ใช้ตรวจสอบ:

- Open Ports
- Running Services
- OS Detection
- Service Versions

---

## 🔍 สามารถตรวจพบ

- Open Ports
- Running Services
- SSL Services
- Vulnerable Versions

---

## ✅ จุดแข็ง

- แม่นยำสูง
- Script Engine (NSE) ทรงพลัง

## ⚠️ ข้อจำกัด

- ไม่ได้เน้น Web Logic Vulnerabilities

## 🎯 เหมาะสำหรับ

- Infrastructure Assessment
- Attack Surface Discovery

</details>

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">4. Feroxbuster</span></summary>

## 📖 ภาพรวม

Feroxbuster เป็น Directory Discovery Tool

ใช้ค้นหา:

- Hidden Directories
- Hidden Files
- Backup Files
- Admin Panels

---

## 🔍 สามารถตรวจพบ

- /admin
- /backup.zip
- /.git
- /config.php

---

## ✅ จุดแข็ง

- เร็วมาก
- Recursive Scan

## ⚠️ ข้อจำกัด

- ใช้ bandwidth สูง

## 🎯 เหมาะสำหรับ

- Content Discovery
- Hidden Endpoint Discovery

</details>

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">5. Gobuster</span></summary>

## 📖 ภาพรวม

Gobuster ใช้สำหรับ brute-force:

- Directories
- Subdomains
- DNS Records

---

## 🔍 สามารถตรวจพบ

- Hidden Paths
- Virtual Hosts
- Backup Files

---

## ✅ จุดแข็ง

- เร็ว
- ใช้งานง่าย

## ⚠️ ข้อจำกัด

- Wordlist quality มีผลต่อผลลัพธ์

## 🎯 เหมาะสำหรับ

- Web Enumeration
- DNS Discovery

</details>

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">6. testssl.sh</span></summary>

## 📖 ภาพรวม

เครื่องมือสำหรับตรวจสอบ:

> SSL/TLS Security

---

## 🔍 สามารถตรวจพบ

- Weak Cipher Suites
- TLS Misconfiguration
- Expired Certificates
- Insecure Protocols

---

## ✅ จุดแข็ง

- แม่นยำมาก
- วิเคราะห์ SSL ได้ละเอียด

## ⚠️ ข้อจำกัด

- ตรวจเฉพาะ SSL/TLS

## 🎯 เหมาะสำหรับ

- HTTPS Security Audit

</details>

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">7. OWASP ZAP</span></summary>

## 📖 ภาพรวม

OWASP ZAP เป็นเครื่องมือ DAST สำหรับ Web Application

สามารถทำ:

- Spidering
- Active Scan
- Passive Scan
- Intercept Proxy

---

## 🔍 สามารถตรวจพบ

- SQL Injection
- XSS
- CSRF
- Authentication Issues

---

## ✅ จุดแข็ง

- ครอบคลุมมาก
- GUI + Automation

## ⚠️ ข้อจำกัด

- ใช้เวลาสแกนนาน

## 🎯 เหมาะสำหรับ

- Web Application Security Testing
- CI/CD Security Testing

</details>

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">8. ffuf</span></summary>

## 📖 ภาพรวม

ffuf เป็น Fast Web Fuzzer

ใช้ fuzzing:

- Directories
- Parameters
- APIs
- Headers

---

## 🔍 สามารถตรวจพบ

- Hidden Parameters
- Hidden APIs
- Hidden Files

---

## ✅ จุดแข็ง

- เร็วมาก
- Flexible สูง

## ⚠️ ข้อจำกัด

- ต้องใช้ wordlist ที่ดี

## 🎯 เหมาะสำหรับ

- API Security Testing
- Parameter Discovery

</details>

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">9. nuclei</span></summary>

## 📖 ภาพรวม

Nuclei เป็น Vulnerability Scanner แบบ Template-based

---

## 🔍 สามารถตรวจพบ

- CVEs
- Misconfiguration
- Exposed Panels
- Sensitive Files

---

## ✅ จุดแข็ง

- Scan เร็ว
- Templates เยอะ

## ⚠️ ข้อจำกัด

- Accuracy ขึ้นกับ template

## 🎯 เหมาะสำหรับ

- Automated Security Testing

</details>

---

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">10. WPScan</span></summary>

## 📖 ภาพรวม

WPScan เป็น Security Scanner สำหรับ WordPress

---

## 🔍 สามารถตรวจพบ

- WordPress Version
- Vulnerable Plugins
- Vulnerable Themes
- Weak Credentials

---

## ✅ จุดแข็ง

- แม่นยำมากกับ WordPress

## ⚠️ ข้อจำกัด

- รองรับเฉพาะ WordPress

## 🎯 เหมาะสำหรับ

- WordPress Security Assessment

</details>

---

# 📊 ตารางเปรียบเทียบเครื่องมือ

| Tool        | Type                  | Scan Speed | Analysis Depth | Automation | เหมาะกับ                  |
| ----------- | --------------------- | ---------- | -------------- | ---------- | ------------------------- |
| CMSeeK      | CMS Scanner           | ⭐⭐⭐⭐   | ⭐⭐⭐         | ✅         | CMS Detection             |
| Nikto       | Web Scanner           | ⭐⭐⭐     | ⭐⭐⭐         | ✅         | Web Server Audit          |
| Nmap        | Network Scanner       | ⭐⭐⭐⭐   | ⭐⭐⭐⭐       | ✅         | Port & Service Discovery  |
| Feroxbuster | Directory Scanner     | ⭐⭐⭐⭐⭐ | ⭐⭐⭐         | ✅         | Hidden Files              |
| Gobuster    | Enumeration           | ⭐⭐⭐⭐⭐ | ⭐⭐⭐         | ✅         | Subdomain & Directory     |
| testssl.sh  | SSL Scanner           | ⭐⭐⭐⭐   | ⭐⭐⭐⭐       | ✅         | HTTPS Audit               |
| OWASP ZAP   | DAST Scanner          | ⭐⭐⭐     | ⭐⭐⭐⭐⭐     | ✅         | Web Security Testing      |
| ffuf        | Fuzzer                | ⭐⭐⭐⭐⭐ | ⭐⭐⭐         | ✅         | API & Parameter Discovery |
| nuclei      | Vulnerability Scanner | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐       | ✅         | CVE Detection             |
| WPScan      | CMS Scanner           | ⭐⭐⭐⭐   | ⭐⭐⭐⭐       | ✅         | WordPress Testing         |

---

# 🚀 Recommended Toolsets

## Web Application Security

```text
OWASP ZAP + Nuclei + ffuf + Nikto
```

ครอบคลุม:

- Vulnerability Scanning
- Hidden Endpoints
- Parameter Discovery
- Server Misconfiguration

---

## CMS Security Testing

```text
CMSeeK + WPScan + Nuclei
```

---

## Infrastructure + Web Discovery

```text
Nmap + Gobuster + Feroxbuster
```

---

## HTTPS / SSL Security

```text
testssl.sh + Nmap
```

---

## 📌 สรุป

DAST ช่วยตรวจสอบช่องโหว่จากมุมมองของผู้โจมตี โดยจำลองการโจมตีระบบจริงขณะที่ Application กำลังทำงานอยู่

การใช้หลายเครื่องมือร่วมกันจะช่วยเพิ่ม Coverage เช่น:

- **Nmap** → Network Discovery
- **Gobuster / Feroxbuster / ffuf** → Content Discovery
- **OWASP ZAP** → Web Vulnerability Testing
- **Nuclei** → CVE Detection
- **testssl.sh** → SSL/TLS Security

การผสมผสานหลายเครื่องมือช่วยเพิ่มประสิทธิภาพในการทำ Web Application Security Assessment และ DevSecOps Testing
