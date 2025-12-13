# Quick Setup Guide

## For New Users

### 1. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/finalChatDoc.git
cd finalChatDoc
```

### 2. Install Dependencies
```bash
# Create virtual environment
python -m venv venv

# Activate it
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install packages
pip install -r requirements.txt
```

### 3. Configure Environment
```bash
# Copy example file
cp .env.example .env

# Edit .env and add your API keys:
# - Get Gemini API key from: https://makersuite.google.com/app/apikey
```

### 4. Run the Application
```bash
uvicorn app:app --reload
```

### 5. Open in Browser
Navigate to: http://localhost:8000

---

## For Deployment on Render

1. **Push to GitHub** (if not already done)
2. **Create Web Service** on Render Dashboard
3. **Connect Repository**
4. **Set Environment Variables**:
   - `GEMINI_API_KEY` = your_gemini_key
   - `FIREBASE_CREDENTIALS` = your_firebase_json (optional)
5. **Deploy!**

---

## Troubleshooting

### "ModuleNotFoundError"
- Make sure virtual environment is activated
- Run: `pip install -r requirements.txt`

### "Missing API Key" Error
- Check your `.env` file exists
- Verify API keys are set correctly
- GEMINI_API_KEY must be set

### Port Already in Use
- Change port: `uvicorn app:app --port 8001`

---

## Features to Test

1. **Chat**: Start a consultation and describe symptoms
2. **Voice**: Try the microphone and speaker features
3. **History**: Check if chat history persists
4. **Summary**: View patient summary

---

## Need Help?

- Check the full README.md for detailed documentation
- Review logs for error messages
- Ensure all dependencies are installed
