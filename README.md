# AI Interview Assistant

A voice-based interview-practice application that asks adaptive interview questions, converts spoken answers to text, reads questions aloud, and provides AI-generated feedback at the end of an interview.

## Features

- Choose an interview topic: Self Introduction, Generative AI, Python, English, HTML, or CSS
- Complete a conversational five-question interview
- Record answers directly from your browser microphone
- Convert speech to text with AssemblyAI
- Generate adaptive questions and final feedback with Google Gemini
- Hear interview questions in a natural voice through Murf AI
- View a score, strengths, and suggested areas for improvement

## Tech stack

- **Frontend:** HTML, JavaScript, Tailwind CSS, Font Awesome
- **Backend:** Python, Flask, Flask-CORS
- **AI and voice services:** Google Gemini, LangChain, LangGraph, AssemblyAI, Murf AI

## Project structure

```text
conversation_platform/
├── backend/
│   ├── app.py              # Flask API and AI interview logic
│   └── requirements.txt    # Python dependencies
├── frontend/
│   ├── index.html          # Application interface
│   └── index.js            # Recording, audio, and API interactions
├── .gitignore
└── README.md
```

## Prerequisites

- Python 3.10 or later
- A modern browser with microphone access enabled
- API keys for:
  - [Google AI Studio](https://aistudio.google.com/) (Gemini)
  - [AssemblyAI](https://www.assemblyai.com/)
  - [Murf AI](https://murf.ai/)

## Installation

1. Clone the repository and enter the project folder.

   ```bash
   git clone <your-repository-url>
   cd conversation_platform
   ```

2. Create and activate a virtual environment.

   **Windows PowerShell:**

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

3. Install the backend dependencies.

   ```bash
   pip install -r backend/requirements.txt
   ```

4. In the project root, create a file named `.env` and add your API keys:

   ```env
   GOOGLE_API_KEY=your_google_ai_api_key
   MURF_API_KEY=your_murf_api_key
   ASSEMBLYAI_API_KEY=your_assemblyai_api_key
   ```

   Keep this file private: `.env` should be included in `.gitignore` and never pushed to GitHub.

## Run the application

1. Start the Flask backend from the project root:

   ```bash
   python backend/app.py
   ```

   The API runs at `http://127.0.0.1:5000`.

2. Open `frontend/index.html` using a local development server. For example, with the VS Code **Live Server** extension, right-click `index.html` and choose **Open with Live Server**.

3. Select a topic, start the interview, allow microphone permission, and submit your spoken answers.

## API endpoints

| Endpoint | Method | Purpose |
| --- | --- | --- |
| `/start-interview` | `POST` | Starts an interview for the selected subject and streams the first spoken question. |
| `/submit-answer` | `POST` | Accepts a recorded audio answer, transcribes it, and streams the next question. |
| `/get-feedback` | `POST` | Generates a score and detailed interview feedback. |

## Environment variables

| Variable | Used for |
| --- | --- |
| `GOOGLE_API_KEY` | Google Gemini interview questions and feedback |
| `MURF_API_KEY` | Text-to-speech interview voice |
| `ASSEMBLYAI_API_KEY` | Speech-to-text transcription |

## Notes

- The application is intended for local development. The frontend API URLs currently point to a Flask server running on port `5000`.
- Your browser must be allowed to access the microphone for answer recording to work.
- Never commit API keys, `.env`, virtual environments, or generated audio files to GitHub.
