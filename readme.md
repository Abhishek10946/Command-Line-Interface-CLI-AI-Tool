# Inline - AI-Powered CLI Terminal

An intelligent command-line interface powered by Groq's AI that helps you execute shell commands using natural language. Get AI suggestions, convert natural language to commands, and enjoy an interactive terminal experience with safety features.

## Features

✨ **AI-Powered Suggestions** - Get intelligent command suggestions using Ctrl+T
🤖 **Natural Language to Commands** - Describe what you want, and Inline converts it to shell commands
⚡ **Fast Execution** - Powered by Groq's high-speed API for instant responses
🛡️ **Safety First** - Built-in protection against dangerous system commands
💾 **Command History** - Smart history tracking with contextual suggestions
🔐 **Environment Variables** - Secure API key management with .env support

## Installation

### Prerequisites
- Python 3.8 or higher
- A free Groq API key from [console.groq.com](https://console.groq.com)

### Setup

1. **Clone or download the project**
   ```bash
   cd d:\PYTHON\Final_CLI_project
   ```

2. **Create a virtual environment** (optional but recommended)
   ```bash
   python -m venv .venv
   .\.venv\Scripts\activate  # Windows
   source .venv/bin/activate  # macOS/Linux
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure your Groq API key**
   - Create a `.env` file in the project root
   - Add your API key:
     ```
     GROQ_API_KEY=your_api_key_here
     ```
   - Get a free API key from [console.groq.com](https://console.groq.com)

## Usage

### Start the Application
```bash
python main.py
```

### Available Commands

| Command | Description |
|---------|-------------|
| `inline --help` | Shows this help menu |
| `inline --ask <query>` | Ask the AI a question |
| `inline --execute <query>` | Convert natural language to a command and execute it |
| `Ctrl+T` | Get AI-powered command suggestions |
| `exit` | Quit the application |
| `inline --contact` | Get support contact information |

### Examples

#### Ask the AI
```bash
inline --ask what is the current Python version?
```

#### Execute Natural Language Commands
```bash
inline --execute list all files in the current directory
inline --execute create a new folder called backup
inline --execute find all Python files modified in the last 7 days
```

#### Get Suggestions
Press `Ctrl+T` inside the terminal to get AI suggestions for your next command based on your command history.

## Requirements

All dependencies are listed in `requirements.txt`:

- **groq** (>=0.10.0) - Groq API client
- **prompt_toolkit** (3.0.51) - Interactive command-line interface
- **python-dotenv** (1.1.1) - Environment variable management

## Safety Features

Inline includes built-in protection against dangerous operations:
- Prevents recursive deletion commands (`rm -rf /`, `del /s /q`, etc.)
- Blocks hard drive formatting operations
- Protects against system shutdown/reboot commands
- Prevents registry and boot sector modifications
- Windows and Unix-like systems supported

⚠️ **Note:** Always review AI-suggested commands before execution, especially system-level operations.

## Architecture

The application consists of three main AI functions:

1. **askQuestions()** - Answers user queries using Groq's Llama 3.3 70B model
2. **executeQuery()** - Converts natural language to shell commands
3. **suggest_commands()** - Provides command suggestions based on history

All requests use the `llama-3.3-70b-versatile` model for optimal performance.

## Environment Variables

Create a `.env` file with the following:

```env
GROQ_API_KEY=your_api_key_from_console_groq_com
```

## Troubleshooting

### "GROQ_API_KEY environment variable not set"
- Create a `.env` file in the project directory
- Add your API key: `GROQ_API_KEY=your_key_here`
- Restart the application

### Network Connection Errors
- Check your internet connection
- Verify your Groq API key is valid
- Ensure you haven't exceeded API rate limits

### Command Not Executing
- Review the AI-suggested command before execution
- Check if the command contains dangerous patterns
- Ensure proper syntax for your operating system

## Platform Support

- ✅ **Windows** - Full support with Windows Command Prompt
- ✅ **macOS** - Full support with Bash/Zsh
- ✅ **Linux** - Full support with Bash and other shells

## API Limitations

The Groq free tier provides generous limits:
- Fast response times (ideal for interactive use)
- Per-minute rate limits apply
- No hard daily limit for free tier users

For more details, visit [console.groq.com](https://console.groq.com)

## Contact & Support

For issues, suggestions, or support:
- **Email:** inlineterminal@gmail.com
- Run `inline --contact` in the application

## License

This project is provided as-is for educational and personal use.

## Disclaimer

⚠️ **Important:** This tool executes shell commands. Always review AI-suggested commands before execution. The developers are not responsible for accidental data loss or system damage from command execution. Use at your own risk and always maintain backups of important data.

---

**Built with** ❤️ **using Groq API and prompt_toolkit**
