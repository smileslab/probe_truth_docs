# Upload Media

The `POST /v1/media/upload` endpoint allows you to upload media for deepfake analysis. This is the first step in the ProbeTruth detection pipeline.

You can upload **videos**, **audio**, or **images** for forensic evaluation.

---

## Endpoint

`POST https://api.probetruth.ai/v1/media/upload`

---

## Authentication

This endpoint requires a valid API key. Include it in the `Authorization` header:

`Authorization: Bearer YOUR_API_KEY`

---

## Supported Media Types

- `.mp4` — Video
- `.mp3` — Audio
- `.wav` — Audio
- `.jpg` / `.jpeg` — Image
- `.png` — Image

---

## Headers

| Key            | Value                        |
|----------------|------------------------------|
| Authorization  | Bearer `<your_jwt_token_here>` |
| Content-Type   | multipart/form-data          |

---

## Request Body

| Field        | Type     | Required | Description                            |
|--------------|----------|----------|----------------------------------------|
| file         | file     | Yes      | The media file to be analyzed          |
| media_type   | string   | Yes      | Must be one of: `video`, `audio`, `image` |
| filename     | string   | No       | Optional custom name for the upload    |

---

## Example: Upload Video

```
curl -X POST https://api.probetruth.ai/v1/media/upload \
  -H "Authorization: Bearer <your_jwt_token_here>" \
  -F "file=@/path/to/your/video.mp4" \
  -F "media_type=video"
```

**Response**
```
{
  "upload_id": "b91c0fe3-523d-4d3a-9e0e-17cc81c513ab",
  "media_type": "video",
  "status": "uploaded",
  "message": "Video successfully uploaded and queued for analysis."
}
```

---

## Example: Upload Audio

```
curl -X POST https://api.probetruth.ai/v1/media/upload \
  -H "Authorization: Bearer <your_jwt_token_here>" \
  -F "file=@/path/to/your/audio.wav" \
  -F "media_type=audio"
```

**Response**
```
{
  "upload_id": "845f9ac7-9a71-4fcb-8e25-2b7234c6e3fc",
  "media_type": "audio",
  "status": "uploaded",
  "message": "Audio successfully uploaded and queued for analysis."
}
```

---

## Example: Upload Image

```
curl -X POST https://api.probetruth.ai/v1/media/upload \
  -H "Authorization: Bearer <your_jwt_token_here>" \
  -F "file=@/path/to/your/image.jpg" \
  -F "media_type=image"
```

**Response**
```
{
  "upload_id": "132e894e-772e-4a7e-8617-d6765f982032",
  "media_type": "image",
  "status": "uploaded",
  "message": "Image successfully uploaded and queued for analysis."
}
```
## Error Responses
All endpoints return these common error responses:

400 Bad Request
```
{
  "error": "Invalid file type",
  "allowed_types": ["mp4", "mp3", ...]
}
```
401 Unauthorized

```
{
  "error": "Invalid authentication token"
}
```
413 Payload Too Large
```
{
  "error": "File size exceeds 100MB limit"
}
```
---

## Next Step

Once uploaded, use the returned `upload_id` to query analysis results:

```
GET /v1/report-status?upload_id=<upload_id>
```