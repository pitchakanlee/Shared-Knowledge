# 🔐 Static Application Security Testing (SAST)

## 📌 SAST คืออะไร?

**SAST (Static Application Security Testing)** คือกระบวนการตรวจสอบความปลอดภัยของซอฟต์แวร์โดยการวิเคราะห์:

- Source Code
- Binary Files
- Dependencies
- Configuration Files
- Infrastructure as Code (IaC)

โดย **ไม่จำเป็นต้องรันโปรแกรมจริง**

แนวคิดของ SAST คือ **Shift Left Security** ซึ่งหมายถึงการค้นหาและแก้ไขช่องโหว่ตั้งแต่ช่วงพัฒนา ช่วยลดต้นทุนในการแก้ไขปัญหา และลดความเสี่ยงก่อนนำระบบขึ้นใช้งานจริง (Production)

## 🎯 ตัวอย่างช่องโหว่ที่ SAST สามารถตรวจพบได้

| ประเภทช่องโหว่             | รายละเอียด                                  |
| -------------------------- | ------------------------------------------- |
| SQL Injection              | การแทรกคำสั่ง SQL ผ่าน User Input           |
| Cross-Site Scripting (XSS) | การแทรก JavaScript เพื่อโจมตีผู้ใช้งาน      |
| Command Injection          | การรันคำสั่งระบบผ่าน Input ที่ไม่ได้ตรวจสอบ |
| Hardcoded Secrets          | Password, API Keys ถูกเก็บไว้ใน Source Code |
| Weak Cryptography          | ใช้อัลกอริธึมที่ไม่ปลอดภัย เช่น MD5         |
| Unsafe Function Calls      | การเรียกใช้ Function ที่มีความเสี่ยง        |
| Misconfiguration           | การตั้งค่าระบบที่ไม่ปลอดภัย                 |

# 🛠 เครื่องมือ SAST และ Application Security Tools

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">1. Bandit</span></summary>

## 📖 ภาพรวม

Bandit เป็นเครื่องมือ **SAST สำหรับภาษา Python** โดยเฉพาะ

เครื่องมือนี้ใช้เทคนิค:

> **AST (Abstract Syntax Tree Analysis)**

เพื่อวิเคราะห์โครงสร้างของ Source Code Python และค้นหารูปแบบโค้ดที่อาจก่อให้เกิดความเสี่ยง

## 🔍 ตัวอย่างช่องโหว่ที่ตรวจพบได้

### Hardcoded Password

```python
password = "admin123"
```

**ความเสี่ยง:**  
ข้อมูลสำคัญถูกฝังอยู่ใน Source Code

### Unsafe Function Usage

```python
eval(user_input)
```

**ความเสี่ยง:**  
อาจนำไปสู่ Remote Code Execution (RCE)

### Weak Cryptography

```python
hashlib.md5()
```

**ความเสี่ยง:**  
MD5 เป็นอัลกอริธึมที่ไม่ปลอดภัย

## ✅ จุดแข็ง

- รองรับ Python โดยเฉพาะ
- Scan ได้รวดเร็ว
- ติดตั้งและใช้งานง่าย
- Integrate กับ CI/CD ได้ดี

## ⚠️ ข้อจำกัด

- รองรับเฉพาะ Python
- ไม่เหมาะกับระบบหลายภาษา

## 🎯 เหมาะสำหรับ

- Python Backend
- APIs
- Automation Scripts
</details>

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">2. Semgrep</span></summary>

## 📖 ภาพรวม

Semgrep เป็นเครื่องมือ **SAST แบบ Multi-language**

รองรับหลายภาษา เช่น:

- Python
- Java
- JavaScript
- PHP
- Go
- C/C++
- C#
- TypeScript

ใช้เทคนิค:

> **Pattern Matching + Rule-based Analysis**

## 🔍 ตัวอย่างช่องโหว่ที่ตรวจพบได้

### SQL Injection

```python
query = "SELECT * FROM users WHERE id=" + user_input
```

### Command Injection

```python
os.system(user_input)
```

### Hardcoded Secrets

```python
api_key = "abcd1234"
```

## ✅ จุดแข็ง

- Scan ได้เร็วมาก
- รองรับหลายภาษา
- สามารถเขียน Custom Rules ได้
- มี Community Rules จำนวนมาก

## ⚠️ ข้อจำกัด

- หาก Rule ไม่เหมาะสม อาจเกิด False Positive

## 🎯 เหมาะสำหรับ

- Web Applications
- Enterprise Projects
- DevSecOps Pipelines
</details>

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">3. CodeQL</span></summary>

## 📖 ภาพรวม

CodeQL เป็นเครื่องมือจาก GitHub ที่ใช้:

> **Data Flow Analysis + Semantic Analysis**

CodeQL สามารถวิเคราะห์การไหลของข้อมูลภายในระบบได้ลึกกว่า Pattern Matching ทั่วไป

## 🔍 ตัวอย่างช่องโหว่ที่ตรวจพบได้

### SQL Injection Flow

```text
User Input → Application Logic → Database Query
```

### Path Traversal

```python
open(user_input)
```

### Remote Code Execution

```python
exec(user_input)
```

## ✅ จุดแข็ง

- วิเคราะห์ได้ลึกมาก
- แม่นยำสูง
- เหมาะกับโค้ดขนาดใหญ่

## ⚠️ ข้อจำกัด

- Learning Curve สูง
- Setup ค่อนข้างซับซ้อน

## 🎯 เหมาะสำหรับ

- Enterprise Systems
- Large Codebase
- Security Research
</details>

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">4. cdxgen</span></summary>

## 📖 ภาพรวม

cdxgen ไม่ใช่ SAST โดยตรง แต่เป็นเครื่องมือสำหรับสร้าง:

> **SBOM (Software Bill of Materials)**

SBOM คือรายการ Components และ Dependencies ที่ระบบใช้งาน

## 🔍 สามารถตรวจสอบได้

- Open Source Libraries
- Dependency Versions
- Third-party Packages

## ✅ จุดแข็ง

- รองรับหลายภาษา
- ใช้งานง่าย
- เหมาะกับ Supply Chain Security

## ⚠️ ข้อจำกัด

- ไม่ได้ตรวจ Logic Vulnerabilities

## 🎯 เหมาะสำหรับ

- Dependency Management
- Compliance
- Software Supply Chain Security
</details>

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">5. Gosec</span></summary>

## 📖 ภาพรวม

Gosec เป็นเครื่องมือ **SAST สำหรับภาษา Go**

ใช้ตรวจสอบ Security Issues ใน Source Code

## 🔍 ตัวอย่างช่องโหว่ที่ตรวจพบได้

### Hardcoded Secrets

```go
password := "admin123"
```

### Weak Random

```go
math/rand
```

### Unsafe File Permissions

```go
os.Chmod(file, 0777)
```

## ✅ จุดแข็ง

- Scan ได้รวดเร็ว
- แม่นยำกับภาษา Go

## ⚠️ ข้อจำกัด

- รองรับเฉพาะ Go

## 🎯 เหมาะสำหรับ

- Go Applications
- Microservices
</details>

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">6. Aqua Trivy</span></summary>

## 📖 ภาพรวม

Trivy เป็น Security Scanner จาก Aqua Security

รองรับการตรวจสอบ:

- Container Images
- Dependencies
- Operating System Packages
- Secrets
- Infrastructure as Code

## 🔍 สามารถตรวจพบ

- CVEs
- Misconfiguration
- Secrets Leakage

## ✅ จุดแข็ง

- ครอบคลุมหลายด้าน
- นิยมใน DevSecOps และ Cloud Security

## ⚠️ ข้อจำกัด

- ไม่ใช่ SAST แบบ Source Code โดยตรง

## 🎯 เหมาะสำหรับ

- Docker
- Kubernetes
- Cloud Security
</details>

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">7. Bearer</span></summary>

## 📖 ภาพรวม

Bearer เป็นเครื่องมือด้าน Application Security ที่เน้น:

> **Sensitive Data Discovery + Privacy Risk Analysis**

## 🔍 สามารถตรวจพบ

- API Keys
- Personal Data Exposure
- Sensitive Information Leakage

## ✅ จุดแข็ง

- เหมาะกับระบบที่จัดการข้อมูลสำคัญ
- รองรับ Privacy Compliance

## ⚠️ ข้อจำกัด

- ไม่เน้น Business Logic Vulnerabilities

## 🎯 เหมาะสำหรับ

- APIs
- GDPR Compliance
- Privacy Protection
</details>

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">8. TruffleHog</span></summary>

## 📖 ภาพรวม

TruffleHog เป็นเครื่องมือสำหรับตรวจจับ:

> **Secrets Leakage**

สามารถตรวจสอบได้ทั้ง:

- Source Code
- Git History
- Cloud Repositories

## 🔍 สามารถตรวจพบ

- AWS Keys
- SSH Keys
- Tokens
- API Secrets

## ✅ จุดแข็ง

- ตรวจ Secrets ได้แม่นยำ
- Scan ย้อนหลังใน Git History ได้

## ⚠️ ข้อจำกัด

- ไม่ใช่ SAST แบบเต็มรูปแบบ

## 🎯 เหมาะสำหรับ

- Git Repositories
- DevSecOps
- Secret Management
</details>

<details>
<summary><span style="font-size:1.8em; font-weight:bold;">9. Brakeman</span></summary>

## 📖 ภาพรวม

Brakeman เป็นเครื่องมือ **SAST สำหรับ Ruby on Rails**

## 🔍 สามารถตรวจพบ

- SQL Injection
- Cross-Site Scripting (XSS)
- Mass Assignment
- Unsafe Redirects

## ✅ จุดแข็ง

- แม่นยำสูงกับ Ruby on Rails

## ⚠️ ข้อจำกัด

- รองรับเฉพาะ Ruby on Rails

## 🎯 เหมาะสำหรับ

- Rails Applications

</details>

# 📊 ตารางเปรียบเทียบเครื่องมือ

| Tool       | Type             | Scan Speed | Analysis Depth | Multi-language | CI/CD | เหมาะกับ         |
| ---------- | ---------------- | ---------- | -------------- | -------------- | ----- | ---------------- |
| Bandit     | SAST             | ⭐⭐⭐⭐   | ⭐⭐⭐         | Python         | ✅    | Python Projects  |
| Semgrep    | SAST             | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐       | ✅             | ✅    | DevSecOps        |
| CodeQL     | SAST             | ⭐⭐⭐     | ⭐⭐⭐⭐⭐     | ✅             | ✅    | Enterprise       |
| cdxgen     | SBOM             | ⭐⭐⭐⭐   | ⭐⭐           | ✅             | ✅    | Supply Chain     |
| Gosec      | SAST             | ⭐⭐⭐⭐   | ⭐⭐⭐         | Go             | ✅    | Go Projects      |
| Trivy      | Security Scanner | ⭐⭐⭐⭐   | ⭐⭐⭐         | ✅             | ✅    | Containers       |
| Bearer     | Privacy Scanner  | ⭐⭐⭐⭐   | ⭐⭐           | ✅             | ✅    | API Security     |
| TruffleHog | Secret Scanner   | ⭐⭐⭐⭐   | ⭐⭐           | ✅             | ✅    | Secret Detection |
| Brakeman   | SAST             | ⭐⭐⭐⭐   | ⭐⭐⭐         | Ruby on Rails  | ✅    | Rails Projects   |

# 🔬 วิเคราะห์เชิงเปรียบเทียบ

## 1. ความลึกในการวิเคราะห์

| ระดับ              | Tools                   |
| ------------------ | ----------------------- |
| สูงมาก             | CodeQL                  |
| สูง                | Semgrep                 |
| ปานกลาง            | Bandit, Gosec, Brakeman |
| เฉพาะทาง           | TruffleHog, Bearer      |
| Dependency-focused | Trivy, cdxgen           |

**สรุป:**  
หากต้องการวิเคราะห์ Data Flow หรือ Business Logic ที่ซับซ้อน CodeQL มีประสิทธิภาพสูงที่สุด

## 2. ความเร็วในการ Scan

| ระดับ   | Tools                            |
| ------- | -------------------------------- |
| เร็วมาก | Semgrep, Bandit, Gosec, Brakeman |
| เร็ว    | Trivy, TruffleHog                |
| ปานกลาง | CodeQL                           |

**สรุป:**  
หากต้องการใช้งานใน CI/CD ที่ต้องการผลลัพธ์รวดเร็ว Semgrep เป็นตัวเลือกที่เหมาะสม

## 3. การรองรับหลายภาษา

| ประเภท            | Tools                                              |
| ----------------- | -------------------------------------------------- |
| Multi-language    | Semgrep, CodeQL, Trivy, Bearer, TruffleHog, cdxgen |
| Specific Language | Bandit, Gosec, Brakeman                            |

**สรุป:**  
หากองค์กรมีหลายทีมพัฒนา Semgrep หรือ CodeQL จะเหมาะสมกว่า

# 🚀 Recommended Toolsets

## Web Application Security

```text
Semgrep + CodeQL + TruffleHog + Trivy
```

ครอบคลุม:

- Source Code Security
- Business Logic Analysis
- Secret Detection
- Dependency & Container Security

## Python Projects

```text
Bandit + Semgrep + TruffleHog
```

## Cloud Native / Containers

```text
Trivy + Semgrep + cdxgen
```

## Enterprise Security

```text
CodeQL + Semgrep + Trivy + Bearer
```

## 📌 สรุป

เครื่องมือแต่ละตัวมีความสามารถแตกต่างกัน และไม่ได้แข่งขันกันโดยตรง แต่ทำงานเสริมกัน

ตัวอย่างเช่น:

- **Bandit** → ตรวจ Source Code ภาษา Python
- **Semgrep** → ตรวจ Source Code หลายภาษา
- **CodeQL** → วิเคราะห์ Data Flow และ Logic Vulnerabilities
- **TruffleHog** → ตรวจ Secrets Leakage
- **Trivy** → ตรวจ Dependencies และ Containers

ดังนั้น ในการสร้าง Secure SDLC หรือ DevSecOps Pipeline ควรใช้หลายเครื่องมือร่วมกันเพื่อเพิ่ม Coverage และลดความเสี่ยงด้านความปลอดภัยของระบบ
