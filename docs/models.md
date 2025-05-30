# Detection Models

ProbeTruth leverages a suite of advanced AI models to detect deepfakes across visual, audio, and audiovisual domains. Each model targets specific forgery cues using state-of-the-art machine learning techniques.

---

## Audiovisual Model

### DARL (v1.0)
- **Type:** Audiovisual
- **Focus:** Speech-Lips Synchronization
- **Description:** DARL analyzes the temporal alignment between speech audio and corresponding lip movements in video. It flags inconsistencies that are indicative of synthetic tampering or lip-sync manipulation.

---

## Visual Models

### DBaG-Net (v1.0)
- **Type:** Visual
- **Focus:** Facial Geometry
- **Description:** DBaG-Net detects abnormalities in facial proportions, landmarks, and geometric consistency that are often introduced by deepfake generation processes.

### Atten-ViT (v1.0)
- **Type:** Visual
- **Focus:** Spatial Artifacts
- **Description:** Based on Vision Transformers, Atten-ViT captures subtle pixel-level and regional inconsistencies, such as unnatural textures or blending errors in forged images or video frames.

---

## Audio Models

### Audio-RRL (v1.0)
- **Type:** Aural
- **Focus:** Spectro-temporal Artifacts
- **Description:** Audio-RRL identifies temporal inconsistencies and unnatural frequency patterns in audio, which may result from voice synthesis or manipulation techniques.

### PSA-Net (v1.0)
- **Type:** Aural
- **Focus:** Spectral Artifacts
- **Description:** PSA-Net focuses on spectral analysis to detect discrepancies in voice patterns and harmonics, useful in identifying audio deepfakes.

### Spot-Net (v1.0)
- **Type:** Aural
- **Focus:** Temporal Artifacts
- **Description:** Spot-Net examines voice continuity and timing to detect breaks, delays, or unnatural speech patterns introduced by tampering or generation models.

---

## Model Selection

The appropriate model(s) are automatically selected based on the uploaded media type:
- **Video** → Audiovisual + Visual + Audio Models
- **Image** → Visual Models only
- **Audio** → Audio Models only

Each model contributes its prediction and confidence score to the final decision.

---
