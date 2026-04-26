# scraper - Privacy & Data Removal Tool

scraper is a specialized utility designed to find and request the removal of personal information from people-search websites and data brokers.

## Features
- **Full Web Search**: Uses the Serper API to find mentions of your name, phone, and email across the web.
- **Triple-Lock Safety**: Automatically filters out restricted government and military domains.
- **Auto-Removal Assistant**: Navigates to opt-out pages and attempts to submit removal requests automatically.
- **Stealth Mode**: Uses persistent browser profiles and human-mimicry to bypass bot detection (Cloudflare).
- **Human-in-the-Loop**: Runs in headful mode, allowing you to solve CAPTCHAs manually to ensure the removal process continues.

## Installation
1. Install required dependencies:
   ```bash
   pip install fastapi uvicorn playwright playwright-stealth requests
   ```
2. Install Playwright browsers:
   ```bash
   playwright install chromium
   ```

## Usage

### 1. Start the Server
Run the backend engine:
```bash
python scraper.py
```

### 2. Request a Full Search & Removal
Open a second terminal and send a POST request with your details:

```bash
curl -X POST http://localhost:8000/full_search -H "Content-Type: application/json" -d "{\"name\": \"Your Name\", \"phone\": \"Your Phone\", \"email\": \"your@email.com\"}"
```

### 3. Manual Intervention
When the browser window opens:
- If you see a **"Verify you are human"** or **CAPTCHA** screen, solve it immediately.
- The script will detect the success and continue with the opt-out process.
