# ⚡ Inline Terminal — CLI AI Tool

> An AI-powered command-line terminal. Describe what you want in plain English — the AI writes the commands, sandboxes them in Docker, and runs them only after your confirmation.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)
![Groq](https://img.shields.io/badge/AI-Groq%20LLaMA%203.3-orange?style=flat-square)
![Docker](https://img.shields.io/badge/Sandbox-Docker-2496ED?style=flat-square&logo=docker)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey?style=flat-square)

---

## 📌 Table of Contents

- [✨ Features](#-features)
- [📦 Requirements](#-requirements)
- [🚀 Installation](#-installation)
- [🎮 Usage](#-usage)
- [🔒 How Dangerous Command Detection Works](#-how-dangerous-command-detection-works)
- [🐳 How inline --execute Works](#-how-inline---execute-works)
- [🗂 Project Structure](#-project-structure)
- [📬 Contact](#-contact)

---

## ✨ Features

<details>
<summary><b>🤖 AI Q&A — Ask anything in plain English</b></summary>

```bash
inlineTerminal<C:\Users\you> $ inline --ask how do I list all running ports on Windows
```
The AI answers instantly with concise, actionable CLI advice.

</details>

<details>
<summary><b>⚙️ AI Command Execution — Describe → Generate → Preview → Run</b></summary>

```bash
inlineTerminal<C:\Users\you> $ inline --execute create a folder called projects and initialize a git repo inside it
```
The AI generates the commands, runs them in a Docker sandbox so you see the output safely, then asks for your confirmation before touching your real system.

</details>

<details>
<summary><b>🛡️ Dangerous Command Detection</b></summary>

Patterns like `rm -rf /`, `format C:`, `shutdown /s`, fork bombs, and 25+ others are detected automatically. You get a warning and must explicitly confirm before anything runs.

</details>

<details>
<summary><b>🐳 Docker Sandbox Preview</b></summary>

AI-generated commands run inside an isolated container first:
- No internet access
- 128 MB RAM limit
- 0.5 CPU limit
- 50 process limit (stops fork bombs)

You see the result before it ever touches your machine.

</details>

<details>
<summary><b>🔮 Smart Autocomplete + AI Suggestions</b></summary>

- `Tab` — autocomplete commands and file/folder paths
- `→ Right Arrow` — accept ghost-text inline suggestion
- `Ctrl+T` — fetch AI-predicted next commands based on your history

</details>

<details>
<summary><b>🐍 Virtual Environment Support</b></summary>

```bash
activate ./venv       # activate a Python venv
deactivate            # deactivate current venv
```
Stacks venvs — switching to a new one restores the previous automatically.

</details>

---

## 📦 Requirements

| Requirement | Version |
|---|---|
| Python | 3.8+ |
| Docker | Any (optional, for sandbox) |
| Groq API Key | Free at [console.groq.com](https://console.groq.com) |

**Python packages:**
```bash
pip install groq python-dotenv prompt_toolkit
```

---

## 🚀 Installation

```bash
# 1. Clone the repository
git clone https://github.com/proAbhishek/Command-Line-Interface-CLI-AI-Tool.git
cd Command-Line-Interface-CLI-AI-Tool

# 2. Install dependencies
pip install groq python-dotenv prompt_toolkit

# 3. Add your Groq API key
echo GROQ_API_KEY=your_key_here > .env

# 4. Launch
python main.py
```

> **Get a free Groq API key:** https://console.groq.com

---

## 🎮 Usage

| Command | What it does |
|---|---|
| `inline --help` | Show the full command index |
| `inline --ask <question>` | Ask the AI any CLI question |
| `inline --execute <task>` | AI generates, previews & runs commands |
| `inline --contact` | Show contact info |
| `activate <path>` | Activate a Python virtual environment |
| `deactivate` | Deactivate the current venv |
| `cd <path>` | Change directory |
| `exit` | Quit the terminal |

| Shortcut | Action |
|---|---|
| `Ctrl+T` | AI-predicted command suggestions |
| `Tab` | Autocomplete command or path |
| `→ Right Arrow` | Accept inline ghost-text suggestion |

---

## 🔒 How Dangerous Command Detection Works

The terminal scans every command against **30+ regex patterns** covering:

- **Linux/macOS** — `rm -rf /`, `dd if=/dev/zero`, `mkfs`, fork bombs, `killall`, `halt`, `reboot`
- **Windows** — `format C:`, `del /s /q`, `rmdir /s /q`, `shutdown /s`, `reg delete`, `bcdedit`, `bootrec`
- **macOS** — `diskutil eraseDisk`, `sudo rm -rf /`, `srm -rf /`

If a match is found:
```
POTENTIAL DANGEROUS COMMAND!!
###
Do you want to Continue with the command?(Y/N):
```
Type `Y` to proceed or `N` to cancel.

---

## 🐳 How `inline --execute` Works

```
You type:    inline --execute create a new react app called myapp

     │
     ▼
  AI generates:  ['npx create-react-app myapp', 'cd myapp']

     │
     ▼
  Docker sandbox runs the commands in isolation
  ┌─────────────────────────────────────────┐
  │ --network none  (no internet)           │
  │ --memory 128m   (RAM limit)             │
  │ --cpus 0.5      (CPU limit)             │
  │ --pids-limit 50 (no fork bombs)         │
  └─────────────────────────────────────────┘
  Output is shown to you safely

     │
     ▼
  Do you Want to Continue with Above List of Commands??(Y/N):

     │
     ▼
  Y → Runs on your real system
  N → Cancelled, nothing happens
```

---

## 🗂 Project Structure

```
Command-Line-Interface-CLI-AI-Tool/
├── main.py       # All application logic
├── .env          # GROQ_API_KEY (never committed)
└── README.md
```

---

## 📬 Contact

| | |
|---|---|
| **Team Email** | inlineterminal@gmail.com |
| **Issues** | [Open an issue on GitHub](https://github.com/proAbhishek/Command-Line-Interface-CLI-AI-Tool/issues) |
