# Upload Media

The `POST /v1/media/upload` endpoint allows you to upload media for deepfake analysis. This is the first step in the ProbeTruth detection pipeline.

You can upload **videos**, **audio**, or **images** for forensic evaluation.

---

## Endpoint

`POST https://api.probetruth.ai/v1/media/upload`
This endpoint requires a valid API key. Include it in the `Authorization` header:
`Authorization: Bearer YOUR_API_KEY`

---

## Supported Media Types

- — Video `.mp4` `.mkv` `.avi` `.mov` `.wmv` `.flv` `.webm` 
- — Audio `.mp3` `.wav` `.aac` `.flac` 
- — Image `.jpg` `.png` `.bmp` `.tiff` 
---

## Headers

| Key             | Value                    |
|-----------------|--------------------------|
| `Authorization` | `Bearer YOUR_API_KEY`    |
| `Content-Type`  | `multipart/form-data`    |

---

## Input

Send the media using `multipart/form-data` with the following fields:

| Field        | Type     | Required | Description                            |
|--------------|----------|----------|----------------------------------------|
| `file`       | `file`   |   Yes    | Media file to be analyzed              |
| `media_type` | `string` |   Yes    | One of `video`, `audio`, or `image`    |
| `filename`   | `string` | Optional | Optional custom name for the upload    |

---

## Output

If successful, the API returns a unique media ID and status.

<pre>
```json
{
  "status": "success",
  "media_id": "abc123xyz",
  "message": "Media uploaded successfully."
}
```
</pre>

In case of an error (e.g. unsupported media type or missing fields):

<pre> 
```json 
{ 
  "status": "error",
  "message": "Invalid media type or missing parameters."
} 
``` 
</pre>

---


## Request Example (Python)
<pre> 
```python
import requests

url = "https://api.probetruth.ai/v1/media/upload" 
headers = { 
  'Authorization': 'Bearer YOUR_API_KEY'
   } 
files = { 'file': open('/path/to/your/video.mp4', 'rb') } 
data = { 'media_type': 'video', 'filename': 'my_video_upload' } 
response = requests.post(url, headers=headers, files=files, data=data)

if response.status_code == 200:
  print("Upload Success:", response.json())
else: 
  print("Error:", response.status_code, response.text)
```
</pre>


## Request Example  (cURL)
<pre>
```bash
curl -X POST https://api.probetruth.ai/v1/media/upload \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -F "file=@/path/to/your/media.mp4" \
  -F "media_type=video"
```
</pre>



## Developer Notes

- Use unique filenames to avoid collisions in downstream processing.
- Media larger than 500MB may fail to upload depending on server-side configuration.
- Accepted media types are validated on the backend. If you're unsure, validate the file type before uploading.
- After uploading, you will receive a media_id used in subsequent API calls (inspect, generate report, etc.).
