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

## Example Request (Python)

Here’s a sample using `requests` in Python to authenticate and call an endpoint:

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