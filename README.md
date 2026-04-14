# api-ethics-assignment#  API Ethics Assignment

##  Overview

This repository contains solutions to an API ethics assignment focused on responsible data handling, privacy protection, and ethical data collection. The project demonstrates best practices in identifying Personally Identifiable Information (PII) and auditing an API script for security and compliance.

---

##  Objectives

* Classify and manage sensitive data responsibly.
* Ensure compliance with ethical and legal standards such as GDPR and HIPAA.
* Identify security and Terms of Service (ToS) violations in an API script.
* Implement industry-standard solutions for secure and ethical data processing.

---

##  Repository Structure

```
api-ethics-assignment/
│── answers.md   # Detailed solutions to both tasks
└── README.md    # Project documentation
```

---

##  Task 1: Classification and Handling of PII

The dataset fields were classified into Direct and Indirect PII, with appropriate privacy-preserving actions applied.

| Field           | PII Type       | Action                  |
| --------------- | -------------- | ----------------------- |
| Full Name       | Direct PII     | Dropped                 |
| Email           | Direct PII     | Dropped                 |
| Date of Birth   | Indirect PII   | Masked                  |
| ZIP Code        | Indirect PII   | Masked                  |
| Job Title       | Indirect PII   | Generalized             |
| Diagnosis Notes | Sensitive Data | Pseudonymized & Cleaned |

**Key Principles Applied:**

* Data Minimization
* De-identification and Masking
* Ethical Data Sharing
* Privacy Protection

---

## Task 2: Ethical Audit of the API Script

### Identified Violations

1. **Hardcoded API Key**

   * Risk: Security vulnerability and potential ToS violation.
   * Solution: Store the API key using environment variables.

2. **Excessive Data Collection and Permanent Storage**

   * Risk: Privacy concerns and non-compliance with ethical standards.
   * Solution: Implement rate limiting, anonymization, and data minimization.

### Best Practices Implemented

* Secure credential management using environment variables.
* Anonymization of sensitive data before storage.
* Rate limiting to respect API policies.
* Responsible and ethical data handling.

---

##  Technologies Used

* **Python**
* **Requests Library**
* **Markdown**
* **Git & GitHub**
* **Environment Variables**

---

##  How to Use

###  Clone the Repository

```bash
git clone https://github.com/PallaviGupta811/api-ethics-assignment.git
cd api-ethics-assignment
```

### Set the Environment Variable

**Windows (Command Prompt):**

```cmd
setx HEALTHSTATS_API_KEY "your_api_key_here"
```

**PowerShell:**

```powershell
$env:HEALTHSTATS_API_KEY="your_api_key_here"
```

**macOS/Linux:**

```bash
export HEALTHSTATS_API_KEY="your_api_key_here"
```

---

##  Ethical Standards Followed

* General Data Protection Regulation (GDPR)
* Health Insurance Portability and Accountability Act (HIPAA)
* Data Minimization Principle
* Privacy-by-Design Approach

---

##  Author

**Pallavi Gupta**
📎 GitHub: https://github.com/PallaviGupta811

