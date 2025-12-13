# 🩺 Dr. HealBot - AI Medical Consultation Assistant

Dr. HealBot is an intelligent medical chatbot application that provides preliminary medical guidance, symptom assessment, and health recommendations. It leverages **Google's Gemini 2.0 Flash** model to simulate a natural, empathetic doctor-patient consultation.

## 🚀 Features

- **Natural Conversation**: Simulates a real doctor's consultation flow with one question at a time
- **AI-Powered**: Uses Google's Gemini 2.0 Flash Experimental model for fast, high-quality responses
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
git clone https://github.com/JawadAliAI/ProWellChatDoc.git
cd ProWellChatDoc
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
   # Gemini API Key (Required)
   GEMINI_API_KEY=your_gemini_api_key_here
   
   # Firebase (Optional - for persistent storage)
   # FIREBASE_CREDENTIALS=path/to/serviceAccountKey.json
   ```

3. **Get API Key**:
   - **Gemini API Key**: [https://makersuite.google.com/app/apikey](https://makersuite.google.com/app/apikey)

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

### Option 1: Deploy via Blueprints (Recommended)
1. Fork this repository
2. Go to Render Dashboard -> Blueprints
3. Connect your repo
4. It will automatically detect `render.yaml`
5. Input your `GEMINI_API_KEY` and invalid/dummy `FIREBASE_CREDENTIALS` (if not using Firebase)

### Option 2: Manual Deployment

#### Step 1: Create Web Service on Render

1. Go to [Render Dashboard](https://dashboard.render.com/)
2. Click **"New +"** → **"Web Service"**
3. Connect your GitHub repository
4. Configure the service:

   **Basic Settings:**
   - **Name**: `dr-healbot`
   - **Runtime**: `Docker`
   - **Instance Type**: `Free`

   **Environment Variables:**
   - Key: `GEMINI_API_KEY` | Value: Your Gemini API key
   - Key: `FIREBASE_CREDENTIALS` | Value: Your Firebase credentials JSON (optional)

5. Click **"Create Web Service"**

#### Step 2: Access Your App
You'll get a URL like: `https://dr-healbot.onrender.com`

---

## 🔐 Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `GEMINI_API_KEY` | Gemini API key for AI chat | ✅ Yes |
| `FIREBASE_CREDENTIALS` | Firebase service account JSON or path | ⚠️ Optional |

---

## 📁 File Structure

```
finalChatDoc/
├── app.py                  # FastAPI application
├── index.html              # Frontend interface
├── requirements.txt        # Python dependencies
├── Dockerfile              # Docker configuration
├── render.yaml             # Render deployment config
├── .dockerignore          # Files to exclude from Docker
├── .gitignore             # Files to exclude from Git
├── .env.example           # Example environment variables
├── README.md              # This file
├── serviceAccountKey.json # Firebase credentials (not in Git)
└── data/                  # Local data storage (not in Git)
```

---

## ⚙️ Technology Stack

- **Backend**: FastAPI (Python)
- **AI Models**: Google Gemini 2.0 Flash / Pro (Exclusive)
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
- **Gemini**: Free tier has rate limits but is generally sufficient for demo purposes.

---

## 📝 License

This project is open source and available under the MIT License.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

---

## 👨‍💻 Author

**Jawad Ali**
- GitHub: [@JawadAliAI](https://github.com/JawadAliAI)

---

## ⭐ Show your support

Give a ⭐️ if this project helped you!