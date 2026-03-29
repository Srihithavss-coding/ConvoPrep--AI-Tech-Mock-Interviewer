# AI-Powered Mock Interview Platform

Interviews are just conversations—but they can still be nerve-wracking. **ConvoPrep AI** simplifies the process by letting you practice with an intelligent LLM that speaks back. With our near real-time voice-to-voice feature, you can rehearse your resume highlights and beyond, turning interview anxiety into effortless confidence.
 
This project is a **full-stack AI-powered mock interview platform** that simulates realistic technical interviews. It generates personalized questions from your resume, conducts voice-based interviews with an AI interviewer, supports live coding challenges, and delivers detailed performance feedback. Practice speaking your answers out loud, get real-time feedback, and do it as many times as you want!

---

## 🏗️ System Architecture

The platform follows a decoupled architecture with heavy integration of specialized AI services.

```text
┌─────────────────────────────────────────────────────────┐
│                    React Frontend                        │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌─────────┐ │
│  │  Setup   │→ │Interview │→ │ Feedback │  │ History │ │
│  │  Page    │  │  Page    │  │  Page    │  │  Page   │ │
│  └──────────┘  └──────────┘  └──────────┘  └─────────┘ │
│       ↓              ↓             ↓            ↓       │
│  ┌──────────────────────────────────────────────────┐   │
│  │            Axios API Service Layer               │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────┬───────────────────────────────┘
                   │ HTTP REST API
┌─────────────────────────┴───────────────────────────────┐
│                   Express Backend                        │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌─────────┐ │
│  │  Routes  │→ │Controllers│→│ Services │→ │ Models  │ │
│  └──────────┘  └──────────┘  └──────────┘  └─────────┘ │
│                      ↓                                   │
│  ┌──────────────────────────────────────────────────┐   │
│  │         External AI Services                      │   │
│  │  ┌─────────┐  ┌──────────┐  ┌───────────────┐   │   │
│  │  │ Gemini  │  │ Murf AI  │  │  AssemblyAI   │   │   │
│  │  │  (LLM)  │  │  (TTS)   │  │   (STT)       │   │   │
│  └─────────┘  └──────────┘  └───────────────┘   │   │
│  └──────────────────────────────────────────────────┘   │
│                      ↓                                   │
│  ┌──────────────────────────────────────────────────┐   │
│  │              MongoDB Atlas                        │   │
│  │  ┌──────┐  ┌───────────┐  ┌──────────┐          │   │
│  │  │Users │  │Interviews │  │ Resumes  │          │   │
│  │  └──────┘  └───────────┘  └──────────┘          │   │
│  └──────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────┘
```

---

## ✨ Key Features

| Feature | Description |
| :--- | :--- |
| **Resume-Based Questions** | AI analyzes your uploaded resume and generates highly personalized interview questions. |
| **Voice Interviews** | Listen to questions via AI voice (Murf TTS) and record your verbal answers naturally. |
| **Live Coding** | Built-in Monaco code editor right in the browser for hands-on coding challenges. |
| **AI Scoring** | Instant, detailed performance reports with scores broken down across 5 distinct categories. |
| **Interview History** | Track all past interviews, review previous scores, and read your historical feedback. |
| **Multi-Role Support** | Tailor your experience across roles like Frontend, Backend, Full Stack, Data Analyst, DevOps, and more. |

---

## 🛠️ Tech Stack & Prerequisites

### Core Stack
* **Frontend:** React, Axios
* **Backend:** Node.js, Express
* **Database:** MongoDB Atlas

### External AI Services
* **Google Gemini (LLM):** Powers the brain of the interviewer, handling question generation and contextual scoring.
* **Murf AI (TTS):** Converts text questions into realistic speech from AI interviewer "Natalie".
* **AssemblyAI (STT):** Transcribes your spoken answers back into text for analysis.

---

## 📁 Project Structure

```text
project/
├── client/          # Frontend application (React)
└── server/          # Backend application (Express & Node.js)
```

---

## 🚀 Installation & Setup

### 1. Clone the repository
```bash
git clone <your-repository-url>
cd project
```

### 2. Setup the Backend
Navigate to the server directory and install dependencies:
```bash
cd server
npm install
```
Create a `.env` file in the `server` directory and add your keys:
```env
PORT=5000
MONGODB_URI=your_mongodb_atlas_connection_string
GEMINI_API_KEY=your_google_gemini_api_key
MURF_API_KEY=your_murf_ai_api_key
ASSEMBLYAI_API_KEY=your_assembly_ai_api_key
```
Start the backend server:
```bash
npm start
```

### 3. Setup the Frontend
Open a new terminal, navigate to the client directory, and install dependencies:
```bash
cd client
npm install
```
Create a `.env` file in the `client` directory:
```env
REACT_APP_API_URL=http://localhost:5000/api
```
Start the frontend application:
```bash
npm start
```

---

## 🎯 Core Functionalities

### 1. Upload Resume &  Setup Interview 
Upload a PDF resume and configure your target interview settings. The AI digests your experience and custom-fits the upcoming technical scenario.

### 2. Give your AI Interview
Engage in dynamic Q&A. Listen to questions spoken by the AI voice, record your verbal responses, and tackle live coding prompts directly on the screen.

### 3. Take Feedback & Interview History
Review your performance post-interview. Get a full breakdown of your scoring, read custom advice on where to improve, and view your growth curve via recorded history.

---

> **Note:** This project bridges the gap between passive studying and actual high-pressure tech interviews. Use it to practice out loud as many times as you want—without scheduling constraints or expensive coaching costs!