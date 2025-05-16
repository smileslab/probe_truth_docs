# API Authentication

To use the ProbeTruth API, you must authenticate each request using a valid API key. This ensures secure access to our deepfake detection services and protects your data.

---

## Obtaining an API Key

ProbeTruth provides API keys on request. Please contact us at [demo@probetruth.ai](mailto:demo@probetruth.ai) to request access.

Once approved, you'll receive your API key via email. This key will allow you to authenticate and use all supported API endpoints.

---

## How to Authenticate

Include your API key in the `Authorization` header of each HTTP request, using the **Bearer token** format:

---
## Request Example

Here’s a sample using `requests` in Python to authenticate and call an endpoint:
<pre>
```python
import requests

API_KEY = 'your_api_key_here'
headers = {
    'Authorization': f'Bearer {API_KEY}'
}

response = requests.get('https://api.probetruth.ai/v1/report-status', headers=headers)

if response.status_code == 200:
    print("Response:", response.json())
else:
    print("Error:", response.status_code, response.text)
```
</pre>


---

## Developer Notes

- All endpoints **require authentication** unless explicitly stated otherwise.
- Use **HTTPS** to ensure encryption of your API key.
- Never expose your API key in client-side code or public repositories.
- API keys are **rate-limited**. For sustained use or enterprise access, please contact us.
- Treat your API key like a password. If compromised, **revoke and regenerate** it immediately.

---

## Input

This endpoint does not require a request body. However, it requires the following **header**:

| Header Key     | Type   | Required | Description                   |
|----------------|--------|----------|-------------------------------|
| Authorization  | string |   Yes    | Format: `Bearer YOUR_API_KEY` |

---

## Output

If the API key is valid, the response from a test endpoint (e.g., `/v1/report-status`) will look like:

<pre>
```json
{
  "status": "success",
  "message": "API key is valid."
}
```
</pre>

If the API key is invalid or missing:

<pre> 
```json 
{ 
    "status": "error",
    "message": "Unauthorized. Invalid or missing API key."
} 
``` 
</pre>
---