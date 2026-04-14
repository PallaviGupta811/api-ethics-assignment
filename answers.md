## Task 1 — Classify and Handle PII Fields

| Field Name      | PII Type                 | Action Taken         | Justification |
|-----------------|--------------------------|----------------------|---------------|
| full_name       | Direct PII               | Drop                 | Directly identifies an individual and is unnecessary for research purposes. |
| email           | Direct PII               | Drop                 | Personally identifiable and not required for analytical use. |
| date_of_birth   | Indirect PII             | Mask                 | Converted to age or age groups to protect privacy while preserving analytical value. |
| zip_code        | Indirect PII             | Mask                 | Reduced to a broader geographic level to prevent re-identification. |
| job_title       | Indirect PII             | Generalize/Mask      | Aggregated into broader categories to maintain privacy. |
| diagnosis_notes | Indirect PII (Sensitive) | Pseudonymize & Clean | Sanitized to remove identifiers while retaining medical insights. |

**Summary:**
Direct PII is removed, while indirect PII is masked or generalized. Sensitive health data is pseudonymized to ensure ethical handling and compliance with privacy regulations such as GDPR and HIPAA.

## Task 2 — Audit the API Script for Ethical Compliance

### Violation 1: Hardcoded API Key

**Problem:**
The API key is hardcoded in the script, posing a security risk and potentially violating the API provider’s Terms of Service. If exposed in a public repository, it could be misused.

**Corrected Code:**
import os
import time
import requests

API_URL = "https://healthstats-api.example.com/records"
API_KEY = os.getenv("HEALTHSTATS_API_KEY")

if not API_KEY:
    raise ValueError(
        "API key not found. Please set the HEALTHSTATS_API_KEY environment variable."
    )

def anonymize_record(record):
    """Remove or mask personally identifiable information."""
    return {
        "patient_id": hash(record.get("email", "")),
        "age": 2026 - int(record["date_of_birth"].split("-")[0]),
        "zip_code": record.get("zip_code", "")[:3] + "XX",
        "job_title": record.get("job_title", "Unknown"),
        "diagnosis_notes": record.get("diagnosis_notes", "")
    }

records = []

for page in range(1, 101):
    response = requests.get(
        API_URL,
        params={"page": page, "key": API_KEY},
        timeout=10
    )
    response.raise_for_status()

    data = response.json()
    anonymized = [
        anonymize_record(r) for r in data.get("results", [])
    ]
    records.extend(anonymized)

    # Respect API rate limits
    time.sleep(1)

# Store only anonymized data
save_to_database(records)
