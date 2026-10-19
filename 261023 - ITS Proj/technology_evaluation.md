# My Technology Test / Replication Notes — Rehabilitation Posture Guidance

## 1. MediaPipe Pose / BlazePose — **P1**

`Camera → 33 landmarks → angles / alignment rules → feedback`

| Test item | Result |
|---|---|
| Quality | GHUM Full — Yoga `62.6 mAP / 95.5 PCK@0.2`; Dance `67.4 / 96.3`; HIIT `68.0 / 95.7` |
| Speed | Full — `25 ms` Pixel 3 TFLite GPU; `27 ms` 2017 MacBook Pro. Lite — `20 / 25 ms` |
| Deployment | Python / Android / web / local CPU or GPU |
| Cost | No per-frame fee |

**Pros:** Local, real-time, 33 landmarks, visible angle rules

**Cons:** Rules need review

## 2. MoveNet — **P2**

`Camera → 17 keypoints → rules / classifier → feedback`

| Test item | Result |
|---|---|
| Speed | Lightning + Thunder — `30+ FPS` on most modern desktops, laptops, phones |
| Variants | Lightning: lower latency; Thunder: higher accuracy |
| Deployment | TensorFlow Hub / TensorFlow Lite / local mobile |
| Cost | No per-request fee |

**Pros:** Lightweight, speed/quality choice

**Cons:** 17 keypoints · no rehab correctness metric

## 3. Ultralytics YOLO11-Pose — **P3**

`Image/video → person + COCO keypoints → custom rules / fine-tuning`

| Test item | Result |
|---|---|
| Quality | COCO Keypoints, 640 px — `50.0 mAP pose 50–95`; `81.0 mAP pose 50` |
| Speed | `52.4 ± 0.5 ms` on CPU, `1.7 ± 0.0 ms` on GPU |
| Size | `2.9M` parameters · `7.5B` FLOPs |
| Deployment | Training + validation + inference, more suitable for laptop/PC |

**Pros:** Trainable, flexible  
**Cons:** Needs labels/training/GPU, greater engineering cost

## 4. OpenAI API — multimodal models — **P2, feedback layer**

`Selected image(s) + exercise criteria + measured angles → structured explanation`

| Test item | My test focus / expected constraint |
|---|---|
| Capability | Image input, cloud API, structured response possible |
| Accuracy | Depends on prompt |
| Latency | No fixed official end-to-end image-assessment figure → measure project p50/p95 |
| Hardware | Camera/app + network · cloud compute |
| Cost | Usage-based |
| Privacy | Needs image/text uploading |

**Pros:** Fast feedback prototype, flexible wording, no custom training  
**Cons:** Network/API dependency, expensive, privacy concerns, high prompt quality required

## Priority summary

| Technology | Local | My test focus | Explainable | Extra data | Priority |
|---|---:|---|---:|---:|---|
| MediaPipe Pose | ✓ | Landmark quality + latency | High | Low | **P1** |
| MoveNet | ✓ | Mobile speed | High | Low | **P2** |
| YOLO11-Pose | ✓ | COCO keypoints + runtime | Medium | High | **P3** |
| OpenAI API | ✗ | Feedback quality + response time | Low alone | Low | **P2 (feedback)** |

## Workflow

```
Camera
  ↓
MediaPipe Pose
  ↓
33 body landmarks
  ↓
Joint angles / posture rules
  ↓
Posture result
  ↓
Structured data
  ↓
Language Model API
  ↓
Simple guidance
  ↓
User
```


