# Inspect Media
Once a media file is successfully uploaded using the [Upload Media Endpoints](#media-upload-endpoints), you can initiate deepfake analysis by calling the dedicated inspection endpoint for the specific media type and providing the `upload_id` in the request body.

---
There are separate endpoints to trigger the inspection process based on the type of uploaded media.

### 1. Inspect Video

The `POST /v1/media/inspect/video` endpoint triggers the deepfake analysis pipeline for a previously uploaded video.

Endpoint: 
POST https://api.probetruth.ai/v1/media/inspect/video

#### Authentication

This endpoint requires **JWT-based token authentication** via AWS Cognito.

Include the access token in the `Authorization` header.

Authorization: Bearer `<your_jwt_token_here>`


#### Request Body

| Field       | Type   | Required | Description                                  |
|-------------|--------|----------|----------------------------------------------|
| `upload_id` | string | Yes      | The unique ID of the uploaded video file.    |

**Content-Type:** `application/json`

#### Example Request
```
curl -X POST [https://www.google.com/search?q=https://api.probetruth.ai/v1/media/inspect/video]
(https://www.google.com/search?q=https://api.probetruth.ai/v1/media/inspect/video) \
  -H "Authorization: Bearer <your_jwt_token_here>" \
  -H "Content-Type: application/json" \
  -d '{"upload_id": "b91c0fe3-523d-4d3a-9e0e-17cc81c513ab"}'

```

Example Success Response (Inspection Initiated)
```
{
  "upload_id": "b91c0fe3-523d-4d3a-9e0e-17cc81c513ab",
  "media_type": "video",
  "analysis_status": "queued",
  "message": "Video inspection initiated."
}
```
Example Error Response (Authentication Failed)

```
{
  "error": "Unauthorized",
  "message": "Invalid or missing token."
}
```
Example Error Response (Missing upload_id in Request Body)

```
{
  "error": "Bad Request",
  "message": "The 'upload_id' field is required in the request body."
}
```

Example Error Response (Invalid upload_id)
```
{
  "error": "Not Found",
  "message": "Video with upload ID 'invalid-id' not found."
}
```

Example Error Response (Incorrect Media Type)

```
{
  "error": "Invalid Request",
  "message": "Upload ID 'some-id' does not correspond to a video file."
}
```

### 1. Inspect Audio
The POST /v1/media/inspect/audio endpoint triggers the deepfake analysis pipeline for a previously uploaded audio file.

Endpoint: 
POST [https://api.probetruth.ai/v1/media/inspect/audio](https://api.probetruth.ai/v1/media/inspect/audio)
This endpoint requires JWT-based token authentication via AWS Cognito.

#### Authentication

This endpoint requires **JWT-based token authentication** via AWS Cognito.

Include the access token in the `Authorization` header.

Authorization: Bearer `<your_jwt_token_here>`

#### Request Body

| Field       | Type   | Required | Description                                  |
|-------------|--------|----------|----------------------------------------------|
| `upload_id` | string | Yes      | The unique ID of the uploaded video file.    |

**Content-Type:** `application/json`

#### Example Request

```
curl -X POST [https://api.probetruth.ai/v1/media/inspect/audio](https://api.probetruth.ai/v1/media/inspect/audio) \
  -H "Authorization: Bearer <your_jwt_token_here>" \
  -H "Content-Type: application/json" \
  -d '{"upload_id": "845f9ac7-9a71-4fcb-8e25-2b7234c6e3fc"}'
```

Example Success Response (Inspection Initiated)
```
{
  "upload_id": "845f9ac7-9a71-4fcb-8e25-2b7234c6e3fc",
  "media_type": "audio",
  "analysis_status": "queued",
  "message": "Audio inspection initiated."
}
```

Example Error Response (Authentication Failed)
```
{
  "error": "Unauthorized",
  "message": "Invalid or missing token."
}
```

Example Error Response (Missing upload_id in Request Body)
```
{
  "error": "Bad Request",
  "message": "The 'upload_id' field is required in the request body."
}
```

Example Error Response (Invalid upload_id)
```
{
  "error": "Not Found",
  "message": "Audio with upload ID 'invalid-id' not found."
}
```
Example Error Response (Incorrect Media Type)
```
{
  "error": "Invalid Request",
  "message": "Upload ID 'some-id' does not correspond to an audio file."
}
```

### 1. Inspect Image

The POST /v1/media/inspect/image endpoint triggers the deepfake analysis pipeline for a previously uploaded image file.

Endpoint: 
POST [https://api.probetruth.ai/v1/media/inspect/image](https://api.probetruth.ai/v1/media/inspect/image)
#### Authentication

This endpoint requires **JWT-based token authentication** via AWS Cognito.

Include the access token in the `Authorization` header.

Authorization: Bearer `<your_jwt_token_here>`

#### Request Body

| Field       | Type   | Required | Description                                  |
|-------------|--------|----------|----------------------------------------------|
| `upload_id` | string | Yes      | The unique ID of the uploaded video file.    |

**Content-Type:** `application/json`

#### Example Request
```
curl -X POST [https://api.probetruth.ai/v1/media/inspect/image](https://api.probetruth.ai/v1/media/inspect/image) \
  -H "Authorization: Bearer <your_jwt_token_here>" \
  -H "Content-Type: application/json" \
  -d '{"upload_id": "132e894e-772e-4a7e-8617-d6765f982032"}'
```

Example Success Response (Inspection Initiated)
```
{
  "upload_id": "132e894e-772e-4a7e-8617-d6765f982032",
  "media_type": "image",
  "analysis_status": "queued",
  "message": "Image inspection initiated."
}
```

Example Error Response (Authentication Failed)
```
{
  "error": "Unauthorized",
  "message": "Invalid or missing token."
}
```

Example Error Response (Missing upload_id in Request Body)
```
{
  "error": "Bad Request",
  "message": "The 'upload_id' field is required in the request body."
}
```

Example Error Response (Invalid upload_id)
```
{
  "error": "Not Found",
  "message": "Image with upload ID 'invalid-id' not found."
}
```

Example Error Response (Incorrect Media Type)
```
{
  "error": "Invalid Request",
  "message": "Upload ID 'some-id' does not correspond to an image file."
}
```
