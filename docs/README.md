# LLM-HackBox

*(formerly developed under the codename "InternBot")*

A deliberately insecure, locally-hosted LLM chat application built to demonstrate, exploit, and remediate real-world vulnerabilities from the **OWASP Top 10 for LLM Applications (2025)**.

> ⚠️ **For educational/demonstration purposes only.** LLM-HackBox is intentionally vulnerable. Do not deploy it on a public-facing server or use it with real credentials/data.

## Why this project

Most LLM security write-ups are theoretical. LLM-HackBox is a hands-on lab: a working Flask + Ollama chatbot with real, exploitable vulnerabilities, paired with a full exploitation walkthrough and remediation for each one — built to show practical, end-to-end AppSec/AI-security skill rather than just familiarity with the OWASP list.

## Vulnerabilities covered

| Payload category | OWASP mapping | Status |
|---|---|---|
| Ignore Instructions / Direct Prompt Injection | LLM01 – Prompt Injection | ✅ Documented & exploited |
| Fake Admin / System Override | LLM01 – Prompt Injection | ✅ Documented & exploited |
| Reveal System Prompts | LLM07 – System Prompt Leakage | ✅ Documented & exploited |
| HTML Injection | LLM05 – Improper Output Handling | ✅ Documented & exploited |
| Direct Data Exfiltration | LLM01 / LLM05 | ✅ Documented & exploited |

Full exploitation walkthroughs: [`docs/EXPLOITATION.md`](docs/EXPLOITATION.md)
Formal write-up with CVSS scoring: [`docs/InternBot_Security_Assessment_Report.docx`](docs/InternBot_Security_Assessment_Report.docx)

## Architecture

```
Browser (chat UI)
      │
      ▼
Flask app (web/app.py)  ──►  Ollama (llama3.2:1b)
      │
      ▼
Docker Compose (local orchestration)
```

## Tech stack

- **Backend:** Python / Flask
- **LLM runtime:** Ollama (`llama3.2:1b`)
- **Orchestration:** Docker Compose
- **Environment:** macOS (M4 Mac Mini)

## Getting started

```bash
git clone https://github.com/nullPrivilege15/LLM-HackBox.git
cd LLM-HackBox
cp .env.example .env        # fill in local config
docker compose up
```

App will be available at `http://localhost:5000` (adjust to your configured port).

## Project structure

```
LLM-HackBox/
├── web/                   # Flask application + UI
│   ├── app.py
│   ├── Dockerfile
│   ├── requirements.txt
│   ├── static/
│   └── templates/
├── docs/
│   ├── EXPLOITATION.md              # Step-by-step exploit walkthroughs
│   ├── InternBot_Security_Assessment_Report.docx  # Formal CVSS-scored report
│   ├── phase-1-foundation.md
│   ├── phase-1-part-2-Step-3.md
│   └── payloads/                    # Evidence per vulnerability category
│       ├── Direct Exfiltration/
│       ├── Fake Admin Override/
│       ├── HTML Injection/
│       ├── Ignore_Instructions/
│       └── Reveal System Prompts/
└── docker-compose.yml
```

## Exploitation & remediation

Full writeup: [`docs/EXPLOITATION.md`](docs/EXPLOITATION.md) — each vulnerability covers the vulnerable code path, a reproducible exploit, its impact, and the fix.

## Disclaimer

This project is built strictly for security research, training, and portfolio demonstration. All testing was performed against a local, self-hosted instance with no real user data.

## Author

**Tathagat** — Application Security Engineer
[LinkedIn](#) · [Portfolio](#)
