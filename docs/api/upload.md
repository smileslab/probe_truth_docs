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

| Key             | Value                    |
|-----------------|--------------------------|
| `Authorization` | `Bearer YOUR_API_KEY`    |
| `Content-Type`  | `multipart/form-data`    |

---

## Request Body

| Field        | Type     | Required | Description                            |
|--------------|----------|----------|----------------------------------------|
| `file`       | `file`   | ✅ Yes   | Media file to be analyzed              |
| `media_type` | `string` | ✅ Yes   | One of `video`, `audio`, `image`      |
| `filename`   | `string` | Optional | Optional custom name for the upload    |

> The media must be sent as `multipart/form-data`.

---

## Example Request (cURL)

```bash
curl -X POST https://api.probetruth.ai/v1/media/upload \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -F "file=@/path/to/your/media.mp4" \
  -F "media_type=video"

