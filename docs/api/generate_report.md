# Generate Forensic Report

After completing the media inspection, you can generate a comprehensive PDF report summarizing the results of the deepfake detection process. This report can be downloaded and printed for legal, forensic, or internal documentation purposes.

---

## How It Works

Once the media has been analyzed and predictions are available, clicking the **"Generate Report"** button will:

1. Compile all analysis results.
2. Structure the content into a formal forensic report.
3. Provide a downloadable **PDF file** with optional print support.

---

## Report Contents

The generated report includes the following sections:

#### 1. General Information
- Media ID
- Upload timestamp
- Media type (video, audio, image)
- File name and format
- User or API key identifier (if applicable)

#### 2. Metadata Information
- Resolution / duration / size
- File properties and encoding format
- Hash or unique media signature

#### 3. Model Analysis Summary
- List of models used for analysis
- Individual predictions with confidence scores
- Verdicts (e.g., Authentic / Deepfake)

#### 4. Explanation &  Evidence
- Key frame thumbnails (for video/image)
- Audio waveform or spectrogram (for audio)
- Highlighted anomalies (if supported)

#### 5. Final Verdict
- Overall decision (e.g., Deepfake Detected)
- Confidence level
- Timestamp of decision

---

> The report is digitally signed and watermarked with the ProbeTruth seal to ensure authenticity.

---

## Download & Print

- The generated report is available in **PDF format**.
- Users can **download** or **print** directly from the browser.
- Reports can also be accessed later via the media history panel (if enabled).



## Endpoint

`POST https://api.probetruth.ai/v1/report/generate`

---

## Headers

| Key             | Value                    |
|-----------------|--------------------------|
| `Authorization` | `Bearer YOUR_API_KEY`    |
| `Content-Type`  | `application/json`       |

---

## Request Body

| Field       | Type     | Required | Description                                  |
|-------------|----------|----------|----------------------------------------------|
| `media_id`  | `string` |   Yes    | The ID of the media file to generate report for |

<pre>
```json
{
  "media_id": "123456789abcdef"
}
```
</pre>



---

## Response

| Field      | Type     | Description                             |
|------------|----------|-----------------------------------------|
| `pdf_file` | binary   | PDF file stream in response body        |
| `status`   | string   | `"success"` or `"error"`                |
| `message`  | string   | Any descriptive message if failed       |

---


## Request Example (Python)
<pre>
```python
import requests

API_KEY = 'your_api_key_here'
MEDIA_ID = '123456789abcdef'

headers = {
    'Authorization': f'Bearer {API_KEY}',
    'Content-Type': 'application/json'
}

data = {
    'media_id': MEDIA_ID
}

response = requests.post('https://api.probetruth.ai/v1/report/generate', headers=headers, json=data)

if response.status_code == 200:
    with open('forensic_report.pdf', 'wb') as f:
        f.write(response.content)
    print("Report downloaded successfully.")
else:
    print("Error:", response.status_code, response.text)


```
</pre>

---

## Developer Notes

- This endpoint will return the PDF file directly in the response body as a binary stream.
- Ensure you write the response content to a .pdf file on your local system.
- Make sure the analysis is complete before calling this endpoint — otherwise you may receive an error.