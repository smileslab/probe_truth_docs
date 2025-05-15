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

- **API Keys**: All endpoints require authentication via secure API keys.
- **Rate Limiting**: To prevent abuse, API usage is rate-limited and monitored.
- **Token Expiry**: Temporary access tokens (when used) expire automatically to reduce risk.

---

## Integrity Protection

- **Hash Verification**: Media file integrity is checked using SHA-256 hash comparison during upload.
- **Tamper Detection**: We monitor anomalies in model execution that may indicate malicious inputs.

---

## Questions?

For inquiries related to security or privacy compliance, contact our security team at:

 **security@probetruth.ai**
