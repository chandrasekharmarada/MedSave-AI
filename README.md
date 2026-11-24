# MedSave AI

**AI-Driven Public Health Chatbot for Disease Awareness with Real-Time Physiological Device Integration**

MedSave AI is a web app that combines an AI health chatbot with live readings from Bluetooth health devices. The chatbot can see your current heart rate or blood pressure and explain what it means in simple language.

> **Disclaimer:** For health awareness and education only. It does not diagnose, prescribe medicine, or suggest dosages. In an emergency, contact local emergency services or a doctor.

---

## What It Is Used For

- Asking general health questions about symptoms, hygiene, nutrition and disease prevention
- Understanding what a heart-rate or blood-pressure reading means
- Learning about common diseases through awareness cards and daily health tips
- Calculating BMI and daily water intake

## How It Helps

- **Easy access to health information**, especially for people who can't easily reach a doctor for simple questions
- **Personalised answers**, because the chatbot uses your live vitals instead of giving generic replies
- **Safety first**: the AI never diagnoses, and it gives emergency guidance for red-flag symptoms like chest pain or breathing difficulty
- **No app or driver needed**, since it runs in the browser and connects to devices directly
- **Always available**, because a built-in demo mode works even without an API key or internet access to the AI

## How It Works

1. The user opens the dashboard and asks a health question in the chatbot.
2. Optionally, on the **Live Reading** page, the user connects a heart-rate monitor, a blood-pressure cuff or a microphone stethoscope.
3. The live vitals are decoded in the browser and shown on screen.
4. When a chat message is sent, the browser sends the message, chat history and vitals to the Express server (`POST /api/chat`).
5. The server adds a safety instruction and calls the Google Gemini API. The API key stays on the server only.
6. Gemini's reply is sent back and shown in the chat window.
7. If Gemini is unavailable or no key is set, a rule-based demo responder answers instead.

## Features

- AI chatbot powered by Google Gemini, with text, voice and image input
- Bluetooth heart-rate monitor support (BLE Heart Rate Service `0x180D`)
- Bluetooth blood-pressure cuff support (BLE Blood Pressure Service `0x1810`, IEEE-11073 SFLOAT decoding)
- Microphone / digital stethoscope pulse estimate using the Web Audio API (experimental)
- Safety guardrails: non-diagnostic answers and emergency escalation
- Rate limiting on the chat endpoint (20 requests per minute)
- Demo mode fallback
- Disease-awareness cards, health tips, BMI and water calculator, language selector

## Tech Stack

| Category | Technology |
| --- | --- |
| Backend | Node.js (18+), Express 4.19 |
| Middleware | cors, dotenv, express-rate-limit |
| AI | Google Gemini API (`gemini-2.5-flash`) |
| Frontend | HTML5, CSS3 (glassmorphism UI), JavaScript (ES6) |
| Browser APIs | Web Bluetooth, Web Audio, getUserMedia |
| Storage | Browser localStorage (demo login session) |

## Pages

| Page | Purpose |
| --- | --- |
| `index.html` | Landing page |
| `login.html` / `signup.html` | Login and sign up |
| `dashboard.html` | Chatbot, awareness cards, health tips |
| `live-reading.html` | Connect Bluetooth devices and microphone, view live vitals |

## Getting Started

```bash
git clone https://github.com/chandrasekharmarada/MedSave-AI.git
cd MedSave-AI
npm install
```

Create a `.env` file:

```env
GEMINI_API_KEY=your_api_key_here
GEMINI_MODEL=gemini-2.5-flash
PORT=3000
```

Start the app:

```bash
npm start
```

Open **http://localhost:3000**. Leave `GEMINI_API_KEY` empty to run in demo mode. Use Chrome or Edge for Bluetooth features.

## Limitations

- Login is a front-end demo only (stored in `localStorage`)
- The microphone pulse estimate is experimental and affected by noise
- Web Bluetooth works only in Chrome and Edge, not Safari or Firefox
- AI answers depend on the Gemini service being available
