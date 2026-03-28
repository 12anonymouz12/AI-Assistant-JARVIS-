# JARVIS V2 - Intelligent Personal AI Assistant

A Flask-based web application with a cyberpunk HUD interface that integrates multiple AI models to provide conversational assistance, document generation, and file automation.

<img width="1227" height="862" alt="image" src="https://github.com/user-attachments/assets/aabb889e-41ae-44ef-b23a-fe8917eb133b" />


## Overview

JARVIS V2 is an intelligent assistant that combines:
- Multi-model AI (Gemini → Groq → Local Mistral fallback)
- Document automation (Word docs, PowerPoint presentations)
- File operations (create, edit, delete files and folders)
- Email sending (smart HTML formatting)
- Persistent memory (full conversation history)
- Futuristic UI (cyan/blue cyberpunk HUD)

## Core Features

### 1. Conversational AI with Memory
- Chat interface with full conversation history persistence
- Multi-model AI fallback (Gemini → Groq → Local Mistral)
- Jarvis persona remembers all previous requests and academic context
- Real-time typing animation with markdown rendering

### 2. Document Generation
- Word Documents (.docx): Create essays, reports, academic notes with AI-generated content
- PowerPoint Presentations (.pptx): Generate multi-slide decks with dynamic images
- AI intelligently parses user intent and auto-creates files
- Files automatically open in desktop application after generation

### 3. File & Folder Operations
- Create, edit, read, and delete text files
- Create and delete folders
- Safe filename sanitization and path traversal protection
- All files stored in created_files/ directory

### 4. Email Operations
- Send formatted HTML emails via Gmail SMTP
- AI improves subject lines and body formatting
- Professional email templates with inline styling

### 5. Intelligent Operation Confirmation
- Detects user intent via regex patterns
- AI parses request details into structured JSON
- Shows summary and asks for confirmation (yes/no)
- Thread-safe operation handling

### 6. Session Management
- Unique session IDs per user
- Tracks pending operations per session
- Fallback handling for multiple concurrent sessions

## Tech Stack

- Backend: Flask, Python 3.8+
- Database: SQLite3
- Document Generation: python-pptx, python-docx
- AI Models: Google Gemini 2.5 Flash, Groq LLaMA 3.3 70B, Local Ollama (Mistral)
- Email: smtplib + SMTP (Gmail)
- Frontend: Vanilla JavaScript, HTML5, CSS3
- Styling: Cyberpunk HUD theme (cyan #00d4ff, #0099ff)

## Installation

Prerequisites:
- Python 3.8+
- Chrome browser (for app mode)
- Gmail account with App Password (for email functionality)
- Optional: Local Ollama with Mistral model (for offline AI)

Setup:
1. Clone/download project
   cd JARVIS\ V2

2. Install dependencies
   pip install flask requests python-pptx python-docx google-generativeai

3. Set API keys in app.py (lines 21-24)
   GEMINI_KEY = "your_gemini_key"
   GROQ_KEY = "your_groq_key"
   SENDER_EMAIL = "your_email@gmail.com"
   SENDER_PASSWORD = "your_app_password"

4. Run application
   python app.py
   - Opens automatically in Chrome at http://127.0.0.1:5000
   - SQLite database created automatically

## Usage Examples

Chat with Memory:
User: "Hey Jarvis"
Jarvis: "Good morning, Sir! Ready to assist with your academic needs."

Create Document:
User: "create a doc on machine learning"
Jarvis: "📝 Document Creation: Topic: machine learning - Proceed? (yes/no)"
User: "yes"
Jarvis: "✅ Document 'machine learning' is ready, Sir."
→ Automatically opens in Word

Generate Presentation:
User: "ppt on artificial intelligence"
Jarvis: "🎫 PowerPoint Creation: Topic: artificial intelligence - Proceed? (yes/no)"
User: "yes"
Jarvis: "✅ The presentation on artificial intelligence is ready, Sir."
→ Automatically opens in PowerPoint

Send Email:
User: "send email to professor@example.com about assignment extension"
Jarvis: "📧 Email Operation: To: professor@example.com - Proceed? (yes/no)"
User: "yes"
Jarvis: "✅ Smart formatted email sent to professor@example.com, Sir."

File Operations:
User: "create a file called notes.txt with content about databases"
Jarvis: [parses and creates file]

## Project Structure

JARVIS V2/
├── app.py                    # Flask backend (820 lines)
├── templates/
│   └── index.html           # Frontend UI (400+ lines)
├── created_files/           # Output directory (auto-created)
└── memory.db                # SQLite chat history (auto-created)

## API Endpoints

GET / → Serve index.html
POST /chat → Main chat handler
GET /status → Return internet status, model, memory count
GET /history → Retrieve chat history
GET /files → List recently created documents/PPTs
GET /open_local/<filename> → Open file in desktop
GET /welcome → Get greeting message

## Security Features

- Path traversal protection for file operations
- Safe filename validation and sanitization
- Email format validation
- Thread locks for concurrent operation safety
- Logging for debugging and error tracking
- Graceful error handling with user-friendly messages
- Flask request context management

## Built For

- Academic document generation
- Study material automation
- Task automation and assistance
- AI-powered tutor with memory

Status: Production-ready with security hardening, logging, and thread safety.
