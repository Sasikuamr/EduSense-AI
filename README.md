# EduSense-AI 🎓🤖  
### Real-Time AI Classroom Engagement & Emotion Intelligence System

EduSense-AI is a full-stack AI-powered classroom analytics platform that measures student engagement, detects emotions, and provides live classroom insights using Computer Vision and Vision Transformers.

The system processes real-time student video streams, classifies emotional states using a Hugging Face Vision Transformer model, computes dynamic engagement scores, and visualizes classroom analytics in an interactive teacher dashboard.

---

# 📸 Application Preview

## 🎥 Student Emotion Detection

### Neutral Detection
<img width="1912" height="1183" alt="Screenshot 2026-02-24 225550" src="https://github.com/user-attachments/assets/eba9627d-3e6b-478f-8582-c97cdbd4a527" />


### Happy Detection
<img width="1919" height="1199" alt="Screenshot 2026-02-24 225603" src="https://github.com/user-attachments/assets/08c64241-b6fb-44e1-ab89-2c18190e8184" />


---

## 🔐 Teacher Login Portal
<img width="1919" height="1174" alt="Screenshot 2026-02-24 225816" src="https://github.com/user-attachments/assets/d847450e-4ff9-4f4e-9447-39afe93d870c" />


---

## 🎓 Student Join Page
<img width="1914" height="1175" alt="Screenshot 2026-02-24 225823" src="https://github.com/user-attachments/assets/36c27d2c-b172-4350-8ca5-e632d0fd1cb8" />


---

# 🏗️ System Architecture

## 🔹 Backend
- Python 3
- FastAPI
- Uvicorn
- WebSockets (real-time communication)
- SQLAlchemy (ORM)
- PostgreSQL (Database)

## 🔹 AI/ML Engine
- OpenCV (Face & Eye Detection)
- Hugging Face Transformers
- `trpakov/vit-face-expression` (Vision Transformer for 7-emotion classification)

## 🔹 Frontend – Teacher Dashboard
- React
- Vite
- Tailwind CSS v4
- Recharts (Live analytics visualization)

## 🔹 Frontend – Student App
- React
- Vite
- Tailwind CSS v4
- WebRTC Camera API (Live frame broadcasting)

---

# ⚙️ How It Works

1. The Student App captures webcam video using WebRTC.
2. Frames are sent to backend via WebSockets.
3. OpenCV detects faces and eyes.
4. Vision Transformer classifies emotion.
5. Engagement score is computed.
6. Data stored in PostgreSQL.
7. Teacher Dashboard updates live via WebSockets.
8. Recharts displays analytics.

---

# 🎭 AI Capabilities

## 7 Detected Emotions

- 😄 Happy  
- 😐 Neutral  
- 😲 Surprise  
- 😢 Sad  
- 😠 Angry  
- 🤢 Disgust  
- 😨 Fear  

The model downloads automatically on first backend boot.

---

# 📊 Engagement Scoring System

**Engagement Score Range:** 0% – 100%  
Calculated up to 10 times per second per student.

### 🔢 Engagement Calculation Logic

#### 1️⃣ Hardware Presence (30%)
- Face detected → +30%
- No face → 0%

#### 2️⃣ Eye Tracking (40%)
- Eyes focused toward screen → +40%

#### 3️⃣ Emotional Context (-10% to +30%)

| Emotion   | Adjustment |
|-----------|------------|
| Happy     | +30% |
| Surprise  | +30% |
| Neutral   | +15% |
| Sad       | +5% |
| Fear      | +5% |
| Disgust   | +5% |
| Angry     | -10% |

Final score is capped at **100%**.

---

# 🚀 Quick Start Guide

You need **3 terminal windows** to run the full stack.

---

## 1️⃣ Start Backend (AI + API + Database Layer)

```bash
cd backend

# Activate virtual environment
.\venv\Scripts\Activate.ps1     # Windows
# source venv/bin/activate      # Mac/Linux

# Start FastAPI server
uvicorn app.main:app --reload --port 8000
