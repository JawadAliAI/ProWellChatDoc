# 🩺 Dr. HealBot - AI Medical Consultation Assistant

Dr. HealBot is an intelligent medical chatbot application designed to provide preliminary medical guidance, symptom assessment, and health recommendations. It leverages advanced AI models to simulate a natural doctor-patient consultation.

## 🚀 Features

- **Natural Conversation**: Simulates a real doctor's consultation flow (Information Gathering -> Diagnosis -> Advice).
- **Voice Interaction**: Supports voice input (Speech-to-Text) and voice output (Text-to-Speech).
- **Patient History**: Remembers patient details and chat history for personalized responses.
- **Medical Knowledge**: Provides advice on symptoms, medications (OTC), and lifestyle.
- **Multi-language Support**: Capable of understanding and responding in multiple languages (via AI).

---

## 📋 Prerequisites for Deployment

1. A [Render account](https://render.com) (free tier available)
2. A [Groq API key](https://console.groq.com) for the AI chatbot
3. Your code pushed to a GitHub repository

---

## 🔧 Deployment Steps (Render)

### Option 1: Deploy via Render Dashboard (Recommended)

#### Step 1: Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit for Render deployment"
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main
```

#### Step 2: Create Web Service on Render

1. Go to [Render Dashboard](https://dashboard.render.com/)
2. Click **"New +"** → **"Web Service"**
3. Connect your GitHub repository
4. Configure the service:

   **Basic Settings:**
   - **Name**: `dr-healbot` (or your preferred name)
   - **Region**: Choose closest to your users
   - **Branch**: `main`
   - **Runtime**: `Docker`
   - **Instance Type**: `Free` (or paid for better performance)

   **Environment Variables:**
   Click **"Advanced"** and add:
   - Key: `GROQ_API_KEY`
   - Value: Your Groq API key
   - Key: `FIREBASE_CREDENTIALS`
   - Value: The content of your `serviceAccountKey.json` (minified JSON string)

5. Click **"Create Web Service"**

#### Step 3: Wait for Deployment

Render will:
- Build your Docker image
- Install dependencies
- Deploy your application

This takes 5-10 minutes for the first deployment.

#### Step 4: Access Your App

Once deployed, you'll get a URL like:
```
https://dr-healbot.onrender.com
```

---

## 🔐 Environment Variables

Make sure to set these in Render Dashboard → Your Service → Environment:

| Variable | Description | Required |
|----------|-------------|----------|
| `GROQ_API_KEY` | Your Groq API key for AI chat | ✅ Yes |
| `FIREBASE_CREDENTIALS` | JSON string of your Firebase service account key | ✅ Yes |
```

---

## 🧪 Testing Your Deployment

### Test the API:
```bash
# Health check
curl https://YOUR_APP.onrender.com/

# Test chat endpoint
curl -X POST https://YOUR_APP.onrender.com/chat \
  -H "Content-Type: application/json" \
  -d '{
    "message": "I have a headache",
    "user_id": "test_user_123",
    "language": "auto"
  }'
```

### Test the Frontend:
Open `https://YOUR_APP.onrender.com/` in your browser

---

## ⚠️ Important Notes

### Free Tier Limitations:
- **Spin down after 15 minutes of inactivity** (first request after spin down takes ~30 seconds)
- **750 hours/month** of runtime
- **Limited resources** (512 MB RAM)

### Data Persistence:
- The `data/` folder stores chat history and patient data locally if Firebase is not used.
- On free tier, local data is **ephemeral** (lost on redeploy).
- **Use Firebase** (configured via `FIREBASE_CREDENTIALS`) for persistent storage.

---

## 🐛 Troubleshooting

### Build Fails:
- Check that all files are committed to GitHub
- Verify `requirements.txt` is present
- Check Render build logs for specific errors

### Application Crashes:
- Check `GROQ_API_KEY` and `FIREBASE_CREDENTIALS` are set correctly
- View logs in Render Dashboard → Your Service → Logs
- Ensure you're not exceeding free tier limits

### Slow Response:
- Free tier spins down after inactivity
- First request after spin down takes 30+ seconds