# 26/10/09

## Workflow

```
Camera / Video
      ↓
Human Posture Understanding
      ↓
Posture / Movement Assessment
      ↓
Identify Problems
      ↓
Corrective Feedback
      ↓
Training Record & Statistics
```

## 1. MediaPipe Pose

**Type:** Pose estimation framework

**Process:**  
Camera → Body landmarks → Joint angles → Posture assessment

**Pros**
- Lightweight / real-time
- Local processing
- Detailed body landmarks
- No custom training required

**Cons**
- No direct judgement
- Need custom angle/rule calculation
- Viewpoint & occlusion sensitivity

**Possible use:**  
Landmarks → joint angles → compare with reference posture

**References**
- [MediaPipe: A Framework for Building Perception Pipelines](https://arxiv.org/abs/1906.08172)
- [BlazePose: On-device Real-time Body Pose Tracking](https://arxiv.org/abs/2006.10204)

---

## 2. MoveNet

**Type:** TensorFlow pose estimation model

**Process:**  
Camera → 17 body keypoints → Posture analysis

**Pros**
- Fast / lightweight
- Lightning & Thunder variants
- TensorFlow Lite support
- Suitable for mobile / edge devices

**Cons**
- Only 17 keypoints
- No direct posture assessment
- Need additional rules / classifier

**Possible use:**  
Keypoints → angles/features → posture classification

**References**
- [MoveNet: Ultra fast and accurate pose detection model](https://www.tensorflow.org/hub/tutorials/movenet)
- [Pose estimation overview](https://www.tensorflow.org/lite/examples/pose_estimation/overview)

---

## 3. Ultralytics YOLO11-Pose

**Type:** Trainable pose estimation framework

**Process:**  
Image/video → Person detection + keypoints → Custom analysis/model

**Pros**
- Real-time pose estimation
- Training / validation / inference supported
- Custom dataset → fine-tuning
- Easy Python integration

**Cons**
- Custom training → labelled dataset
- Higher development workload
- May be unnecessary for simple exercises

**Possible use:**  
Rehabilitation dataset → fine-tune YOLO11-Pose → specialised pose detection

**References**
- [YOLO11 Documentation](https://docs.ultralytics.com/models/yolo11)
- [Pose Estimation Datasets](https://docs.ultralytics.com/datasets/pose)

---

## 4. OpenAI API – Multimodal Models

**Type:** Multimodal AI API

**Process:**  
Posture image + reference + instructions → AI → Assessment / feedback

**Pros**
- No custom model training
- Image + text reasoning
- Flexible for different exercises
- Natural-language feedback

**Cons**
- API cost / Internet dependency
- Privacy considerations
- Non-deterministic output
- Biomechanical accuracy needs validation

**Possible use:**  
User posture + reference posture → structured AI assessment

**References**
- [OpenAI API Platform / Documentation](https://platform.openai.com/docs/)

---

# Quick Comparison

| Technology | Main Feature | Training | Local |
|---|---|---:|---:|
| MediaPipe Pose | Detailed landmarks | No | ✓ |
| MoveNet | Fast keypoint detection | No | ✓ |
| YOLO11-Pose | Customisable pose model | Optional | ✓ |
| OpenAI API | Image reasoning + feedback | No | ✗* |