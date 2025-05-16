
# Generate Forensic Report

After completing the media inspection (see [Initiate Media Inspection Endpoints](#initiate-media-inspection-endpoints)), you can generate a comprehensive PDF report summarizing the results of the deepfake detection process. This report can be downloaded and printed for legal, forensic, or internal documentation purposes.

---

## Endpoint

POST https://api.probetruth.ai/v1/report/generate


---

## Authentication

This endpoint requires **JWT-based token authentication** via AWS Cognito.

Include the access token in the `Authorization` header.

Authorization: Bearer &lt;your_jwt_token_here>


---

## Headers

| Key             | Value                        |
|-----------------|------------------------------|
| `Authorization` | `Bearer <your_jwt_token_here>` |
| `Content-Type`  | `application/json`           |
| `Accept`        | `application/pdf`            |

**Note:** The `Accept: application/pdf` header informs the server that the client expects a PDF file in the response.

---

## Request Body

| Field      | Type     | Required | Description                                  |
|------------|----------|----------|----------------------------------------------|
| `media_id` | `string` | Yes      | The unique ID of the media file to generate the report for. |

**Content-Type:** `application/json`

#### Example Request

```bash
curl -X POST [https://api.probetruth.ai/v1/report/generate](https://api.probetruth.ai/v1/report/generate) \
  -H "Authorization: Bearer <your_jwt_token_here>" \
  -H "Content-Type: application/json" \
  -H "Accept: application/pdf" \
  -d '{"media_id": "b91c0fe3-523d-4d3a-9e0e-17cc81c513ab"}'
```

-----

## Response

**Success Response (HTTP 200 OK)**

The PDF file will be directly streamed in the response body with the `Content-Type: application/pdf` header.

**Example Success Response (Illustrative - Binary Data)**

```

%PDF-1.7
1 0 obj
... (binary PDF data) ...
%%EOF

```

**Error Responses**

| HTTP Status Code | Response Body (JSON)                                     | Description                                                                 |
|------------------|----------------------------------------------------------|-----------------------------------------------------------------------------|
| `401 Unauthorized` | ` json { "error": "Unauthorized", "message": "Invalid or missing token." }  ` | Authentication failed. Ensure a valid JWT token is provided.              |
| `400 Bad Request`  | ` json { "error": "Bad Request", "message": "The 'media_id' field is required." }  ` | The `media_id` field is missing in the request body.                      |
| `404 Not Found`    | ` json { "error": "Not Found", "message": "Media with ID 'invalid-id' not found or analysis not completed." }  ` | The specified `media_id` does not exist or the analysis for it is not yet complete. |
| `500 Internal Server Error` | ` json { "error": "Internal Server Error", "message": "Failed to generate report." }  ` | An unexpected error occurred on the server while generating the report.    |

-----

## Request Example (Python)

```python

import requests

API_TOKEN = 'your_jwt_token_here'
MEDIA_ID = 'b91c0fe3-523d-4d3a-9e0e-17cc81c513ab'

headers = {
    'Authorization': f'Bearer {API_TOKEN}',
    'Content-Type': 'application/json',
    'Accept': 'application/pdf'
}

data = {
    'media_id': MEDIA_ID
}

response = requests.post('[https://api.probetruth.ai/v1/report/generate](https://api.probetruth.ai/v1/report/generate)', headers=headers, json=data, stream=True)

if response.status_code == 200:
    with open(f'forensic_report_{MEDIA_ID}.pdf', 'wb') as pdf_file:
        for chunk in response.iter_content(chunk_size=8192):
            pdf_file.write(chunk)
    print(f"Report for media ID '{MEDIA_ID}' downloaded successfully.")
else:
    print(f"Error generating report for media ID '{MEDIA_ID}':", response.status_code, response.text)

```

-----

## Developer Notes

  - This endpoint returns the PDF file directly in the response body as a binary stream. Ensure your client-side code is capable of handling binary data.
  - The `Accept: application/pdf` header is crucial for indicating the expected response format.
  - Always check the `analysis_status` to ensure the analysis is complete before attempting to generate a report.
  - Error handling is essential to manage scenarios where the media ID is invalid or the report generation fails.

