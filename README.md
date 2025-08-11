# GPT-5-MultiModal

A simple and powerful way to chat with GPT-5 using text, images, or both.

Talk to it.  
Show it images.  
Use quick actions for instant results.  
Keep your conversations going with history.  

---

## What You Can Do

- **Text Chat** – Ask anything, get clear answers.  
- **Image Analysis** – Upload an image, let AI break it down.  
- **Preset Actions** – One-click actions like *Analyze*, *Summarize*, *Describe*, *Extract Text*.  
- **Conversation History** – AI remembers what you discussed earlier.  
- **Multiple Input Methods** – Direct uploads or base64 image input.  

---

## Quick Start

### 1. Setup Environment
Copy the example `.env` file and add your OpenAI API key:

```bash
cp .env.example .env
```

Edit `.env`:
```
OPENAI_API_KEY=your_openai_api_key_here
```

---

### 2. Install Dependencies
This project uses `uv` for dependency management:

```bash
uv sync
```

---

### 3. Run the Backend
```bash
python main.py
```
API runs at: `http://localhost:8000`

Docs:  
- Swagger UI → `http://localhost:8000/docs`  
- ReDoc → `http://localhost:8000/redoc`  

---

## Frontend Setup (React + TypeScript)

### Requirements
- Node.js 16+  
- Backend running on `http://localhost:8000`  

### Install & Run
```bash
cd frontend
npm install
npm start
```

Frontend will be available at: `http://localhost:3000`

---

### Frontend Highlights
- Chat with text and images.  
- Drag & drop image uploads.  
- Quick preset actions after uploading.  
- Syntax-highlighted markdown replies.  
- Copy responses with one click.  
- Works on both mobile and desktop.  

---

## API Endpoints

- **POST /chat/text** – Text-only chat.  
- **POST /chat/image-upload** – Upload image with optional prompt.  
- **POST /chat/image-base64** – Send base64 image for analysis.  
- **GET /presets** – List available quick actions.  
- **POST /chat/multimodal** – Combine text and image in a single request.  

---

## Example Usage

**Python**
```python
import requests

response = requests.post('http://localhost:8000/chat/text', json={
    'message': 'Tell me a joke',
    'conversation_history': []
})
print(response.json()['response'])
```

**JavaScript (React)**
```javascript
const textChat = async (message) => {
  const res = await fetch('http://localhost:8000/chat/text', {
    method: 'POST',
    headers: {'Content-Type': 'application/json'},
    body: JSON.stringify({message, conversation_history: []})
  });
  return await res.json();
};
```

---

## Project Structure

```
GPT-5-MultiModal/
├── main.py              # FastAPI backend application
├── test_api.py          # Backend API test script
├── .env                 # Environment variables (create from .env.example)
├── .env.example         # Environment variables template
├── pyproject.toml       # Backend dependencies
├── README.md            # This file
├── uv.lock             # Backend dependency lock file
└── frontend/            # React frontend application
    ├── public/          # Static assets
    ├── src/             # React source code
    │   ├── App.tsx      # Main React component
    │   ├── App.css      # Main styles
    │   ├── markdown.css # Markdown rendering styles
    │   └── index.tsx    # React entry point
    ├── package.json     # Frontend dependencies
    └── package-lock.json # Frontend dependency lock
```

---

## Tech Stack

**Backend:** FastAPI, OpenAI API, Uvicorn, Pydantic, Requests  
**Frontend:** React 18, Axios, React Dropzone, React Markdown, Lucide Icons, Highlight.js  

---

## Error Handling
- 400 – Invalid input  
- 500 – Server/API error  

---

## Next Steps
- Add authentication and API key limits.  
- Cache frequent responses.  
- Store uploads securely.  
- Add monitoring for production.  
