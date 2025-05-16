# Security & Privacy

At ProbeTruth, safeguarding your data and privacy is at the core of our platform. We are committed to providing a secure, trustworthy environment for detecting deepfakes and protecting digital identity.

---

## Data Handling

- **End-to-End Encryption**: All media uploads and API requests are encrypted using HTTPS (TLS 1.2+).
- **Temporary Storage**: Uploaded media files are stored only for the duration required to complete analysis.
- **Automatic Deletion**: Media files are automatically deleted after inspection and report generation, unless retention is explicitly enabled by the user.

---

## Model Isolation

- Each AI detection model runs in a sandboxed environment to prevent cross-contamination and ensure privacy.
- No raw media data is shared with external systems or third-party services.

---

## Audit & Compliance

- ProbeTruth maintains internal audit logs for critical API events and model decisions.
- We adhere to data protection standards aligned with GDPR and CCPA requirements.

---
## API Security

| Security Feature   | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| **API Keys**        | All endpoints require secure API key authentication.                       |
| **Rate Limiting**   | API usage is throttled to prevent abuse and ensure fair usage.             |
| **Token Expiry**    | Temporary tokens (when issued) have automatic expiration for extra safety. |

---

## Integrity Protection

| Mechanism           | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **Hash Verification** | SHA-256 hash checks are performed on uploaded files to ensure data integrity. |
| **Tamper Detection**  | Internal monitors watch for unusual model behavior or attack patterns.      |

---

## Questions?

For inquiries related to security or privacy compliance, contact our security team at:

 **security@probetruth.ai**
