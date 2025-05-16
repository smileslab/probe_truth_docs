# Media Inspection

Once a media file is successfully uploaded using the `POST /v1/media/upload` endpoint, you can initiate deepfake analysis through the **"Inspect Media"** action in the ProbeTruth interface.

This process automatically triggers backend analysis using multiple AI models, depending on the type of uploaded media (video, audio, or image). No additional API call or input parameters are required at this step.

---
## Backend Behavior
- The system automatically selects the appropriate models based on the uploaded media type.
- No additional input parameters are required from the end-user.
- Status is updated in real time through polling or websocket.
- Internally, model outputs are fused for decision logic.
---

## Workflow

1. **Upload Media**  
   Upload a video, audio, or image file using the `/v1/media/upload` endpoint.

2. **Inspect Media**  
   After upload, click the **"Inspect Media"** button in the ProbeTruth dashboard. This triggers backend analysis.

3. **Model Processing**  
   Based on the type of media:
   - Visual models are run for images/videos.
   - Audio models for audio clips.
   - Audiovisual models for eligible media types.
   
   Each model processes the file in parallel or sequentially, depending on configuration.

4. **Live Feedback**  
   - During analysis, a status bar or loading icon is shown.
   - Once complete, the frontend displays predictions and confidence scores.

---


## Example Response (GUI Display)

![Sample Analysis Output](assets/GUI.png)

---

## Developer Notes

- This inspection step is **automatically triggered** after upload via backend.
- Developers integrating with the API do not need to call a separate endpoint unless setting up custom workflows.
- To poll the inspection status programmatically, use:
`GET /v1/media/status/{media_id}`

---


## Request Example (Python)
<pre>
```python
import requests

media_id = "abc123xyz"
headers = {
    'Authorization': 'Bearer YOUR_API_KEY'
}

response = requests.get(f"https://api.probetruth.ai/v1/media/status/{media_id}", headers=headers)

if response.status_code == 200:
    print(response.json())
else:
    print("Error:", response.status_code)
``` 
</pre>
---
