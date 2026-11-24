# MedSave AI

**AI-Driven Public Health Chatbot for Disease Awareness with Real-Time Device Integration**

MedSave AI is a web app where a Google Gemini-powered chatbot answers health-awareness questions. It can also read live heart rate and blood pressure from Bluetooth devices, so its answers are based on your actual vitals.

> For health awareness only. It does not diagnose or prescribe. In an emergency, call 112 / 108.

## Features

- AI health chatbot (Gemini) with text, voice and image input
- Live heart rate and blood pressure from Bluetooth devices
- Microphone / digital stethoscope pulse estimate
- Safety rules: no diagnosis, emergency guidance for serious symptoms
- Demo mode that works without an API key
- Disease-awareness cards, health tips, BMI and water calculator
- Emergency numbers and first-aid steps
- English, Hindi and Telugu support

## How It Works

1. The user asks a question in the chatbot, optionally with live vitals from a connected device.
2. The browser sends the message and vitals to the Express server.
3. The server adds safety rules and calls the Gemini API. The API key stays on the server.
4. The reply is shown in the chat. If Gemini is unavailable, a built-in demo responder answers instead.

## Tech Stack

- **Backend:** Node.js, Express
- **AI:** Google Gemini API
- **Frontend:** HTML, CSS, JavaScript
- **Browser APIs:** Web Bluetooth, Web Audio

## Run Locally

```bash
git clone https://github.com/chandrasekharmarada/MedSave-AI.git
cd MedSave-AI
npm install
```

Create a `.env` file:

```env
GEMINI_API_KEY=your_api_key_here
```

Then run:

```bash
npm start
```

Open **http://localhost:3000**. Use Chrome or Edge for Bluetooth features. Without an API key, the app runs in demo mode.

## License

MIT
