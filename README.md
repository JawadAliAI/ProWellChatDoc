# 🩺 Dr. HealBot - AI Medical Consultation Assistant

Dr. HealBot is an intelligent medical chatbot application that provides preliminary medical guidance, symptom assessment, and health recommendations. It leverages advanced AI models (Groq's Llama 3.3 and Google's Gemini) to simulate a natural doctor-patient consultation.

## 🚀 Features

- **Natural Conversation**: Simulates a real doctor's consultation flow with one question at a time
- **AI-Powered**: Uses Groq's Llama 3.3 70B model (with Gemini fallback)
- **Voice Interaction**: Supports voice input (Speech-to-Text) and voice output (Text-to-Speech)
- **Patient History**: Remembers patient details and chat history for personalized responses
- **Medical Knowledge**: Provides advice on symptoms, medications (OTC), and lifestyle
- **Hybrid Storage**: Firebase for production, local JSON for development
- **Responsive UI**: Beautiful, modern interface that works on all devices

---

## 📖 How to Use

### 1. Start a Consultation
1. Open the application in your browser
2. Click the **Medical Services** icon (purple button) in the bottom right corner
3. Enter your **Name** to start a session
   - If you've visited before, the app will remember your history

### 2. Chatting with Dr. HealBot
- **Type your symptoms**: Describe what you're feeling (e.g., "I have a headache and fever")
- **Answer Questions**: The doctor will ask clarifying questions one by one
- **Receive Advice**: After gathering enough information, Dr. HealBot will provide a comprehensive summary, possible causes, and advice

### 3. Voice Features 🎤
- **Speak**: Click the **Microphone** icon to speak your message
- **Listen**: The doctor's responses can be read aloud (Text-to-Speech)

### 4. Patient Summary 📋
- Click the **Summary** icon in the header to view your medical profile and consultation summary

---

## 💻 Local Installation & Setup

### Prerequisites
- Python 3.8 or higher
- FFmpeg (for audio processing)

### 1. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/finalChatDoc.git
cd finalChatDoc
```

### 2. Set Up Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Set Up Environment Variables
1. Copy the example environment file:
   ```bash
   cp .env.example .env
   ```

2. Edit `.env` and add your API keys:
   ```env
   # Primary AI Provider (Groq - Fast and Free)
   GROQ_API_KEY=your_groq_api_key_here
   
   # Fallback AI Provider (Optional)
   GEMINI_API_KEY=your_gemini_api_key_here
   
   # Firebase (Optional - for persistent storage)
   # FIREBASE_CREDENTIALS=path/to/serviceAccountKey.json
   ```

3. **Get API Keys**:
   - **Groq API Key** (Recommended): [https://console.groq.com/](https://console.groq.com/)
   - **Gemini API Key** (Optional): [https://makersuite.google.com/app/apikey](https://makersuite.google.com/app/apikey)

### 5. Run the Application
```bash
uvicorn app:app --reload
```

### 6. Access the App
Open your browser and navigate to:
```
http://localhost:8000
```

---

## 🔧 Deployment (Render)

### Option 1: Deploy via Render Dashboard

#### Step 1: Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main
```

#### Step 2: Create Web Service on Render

1. Go to [Render Dashboard](https://dashboard.render.com/)
2. Click **"New +"** → **"Web Service"**
3. Connect your GitHub repository
4. Configure the service:

   **Basic Settings:**
   - **Name**: `dr-healbot`
   - **Region**: Choose closest to your users
   - **Branch**: `main`
   - **Runtime**: `Docker`
   - **Instance Type**: `Free` (or paid for better performance)

   **Environment Variables:**
   Click **"Advanced"** and add:
   - Key: `GROQ_API_KEY` | Value: Your Groq API key
   - Key: `GEMINI_API_KEY` | Value: Your Gemini API key (optional)
   - Key: `FIREBASE_CREDENTIALS` | Value: Your Firebase credentials JSON (optional)

5. Click **"Create Web Service"**

#### Step 3: Wait for Deployment
Render will build and deploy your application (5-10 minutes for first deployment)

#### Step 4: Access Your App
You'll get a URL like: `https://dr-healbot.onrender.com`

---

## 🔐 Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `GROQ_API_KEY` | Groq API key for AI chat (Primary) | ✅ Yes* |
| `GEMINI_API_KEY` | Gemini API key for AI chat (Fallback) | ⚠️ Optional |
| `FIREBASE_CREDENTIALS` | Firebase service account JSON or path | ⚠️ Optional |

*Either `GROQ_API_KEY` or `GEMINI_API_KEY` is required

---

## 📁 File Structure

```
finalChatDoc/
├── app.py                  # FastAPI application
├── index.html              # Frontend interface
├── requirements.txt        # Python dependencies
├── Dockerfile              # Docker configuration
├── .dockerignore          # Files to exclude from Docker
├── .gitignore             # Files to exclude from Git
├── .env.example           # Example environment variables
├── README.md              # This file
├── serviceAccountKey.json # Firebase credentials (not in Git)
└── data/                  # Local data storage (not in Git)
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

## ⚙️ Technology Stack

- **Backend**: FastAPI (Python)
- **AI Models**: 
  - Groq (Llama 3.3 70B Versatile) - Primary
  - Google Gemini 2.0 Flash - Fallback
- **TTS**: Google Text-to-Speech (gTTS)
- **STT**: Google Speech Recognition
- **Database**: Firebase Firestore (optional) / Local JSON
- **Deployment**: Docker, Render

---

## ⚠️ Important Notes

### Free Tier Limitations (Render):
- **Spin down after 15 minutes** of inactivity (first request takes ~30 seconds)
- **750 hours/month** of runtime
- **Limited resources** (512 MB RAM)

### Data Persistence:
- The `data/` folder stores chat history locally if Firebase is not configured
- On free tier, local data is **ephemeral** (lost on redeploy)
- **Use Firebase** for persistent storage in production

### API Rate Limits:
- **Groq**: Generous free tier with fast responses
- **Gemini**: Free tier with rate limits (fallback only)

---

## 🐛 Troubleshooting

### Build Fails:
- Verify all files are committed to GitHub
- Check that `requirements.txt` is present
- Review Render build logs for specific errors

### Application Crashes:
- Ensure `GROQ_API_KEY` or `GEMINI_API_KEY` is set correctly
- View logs in Render Dashboard → Your Service → Logs
- Check you're not exceeding API rate limits

### Slow Response:
- Free tier spins down after inactivity
- First request after spin down takes 30+ seconds
- Consider upgrading to paid tier for always-on service

### Import Errors:
- Make sure all dependencies are in `requirements.txt`
- Verify virtual environment is activated
- Try `pip install -r requirements.txt --force-reinstall`

---

## 📝 License

This project is open source and available under the MIT License.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

---

## 👨‍💻 Author

**Your Name**
- GitHub: [@YOUR_USERNAME](https://github.com/YOUR_USERNAME)

---

## ⭐ Show your support

Give a ⭐️ if this project helped you!