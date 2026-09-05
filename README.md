# Agent2 — Gemini AI Agent

A simple AI agent built with **Python, OpenAI Agents SDK, and Google Gemini**.

This project demonstrates how to configure the OpenAI Agents SDK with Gemini as a third-party AI provider, create an agent with custom instructions, run it asynchronously, and display its response in the terminal.

---

## 🚀 Overview

**Agent2** is a beginner-friendly AI agent project that uses the **OpenAI Agents SDK** with Google's OpenAI-compatible API configuration.

The project creates an AI agent named **Professor** with a teacher-oriented instruction and sends it a predefined question.

The agent's final response is printed directly in the terminal.

---

## ✨ Features

* 🤖 AI agent using OpenAI Agents SDK
* 🧠 Google Gemini integration
* 👨‍🏫 Custom AI agent instructions
* ⚡ Asynchronous agent execution
* 🔄 Gemini configured as an external provider
* 🔐 API key loaded through environment variables
* 💻 Terminal-based output
* 🚫 Agents SDK tracing disabled

---

## 🛠️ Tech Stack

| Technology        | Purpose                           |
| ----------------- | --------------------------------- |
| Python 3.13+      | Programming language              |
| OpenAI Agents SDK | Agent creation and execution      |
| Google Gemini     | AI model                          |
| AsyncOpenAI       | API client configuration          |
| python-dotenv     | Environment variable management   |
| uv                | Dependency and project management |

---

## 📁 Project Structure

```text
Agent2-main/
│
├── README.md
│
└── hello-agent/
    │
    ├── README.md
    ├── pyproject.toml
    ├── uv.lock
    │
    ├── src/
    │   └── hello_agent/
    │       ├── __init__.py
    │       └── agent_hello.py
    │
    └── terminal-ss/
        └── terminal-ss.jpeg
```

---

## 📌 Main File

### `agent_hello.py`

This file contains the actual AI-agent implementation.

It handles:

* Loading environment variables
* Reading the Gemini API key
* Creating an `AsyncOpenAI` client
* Configuring Gemini as the external provider
* Setting the Agents SDK API method
* Disabling tracing
* Creating the AI agent
* Running the agent asynchronously
* Printing the final response

---

## 🧠 How It Works

The project follows this workflow:

```text
User Prompt
     │
     ▼
OpenAI Agents SDK
     │
     ▼
Agent Configuration
     │
     ▼
AsyncOpenAI Client
     │
     ▼
Google Gemini
     │
     ▼
Gemini 2.0 Flash
     │
     ▼
Agent Response
     │
     ▼
Terminal
```

The Gemini API key is loaded from the environment:

```python
load_dotenv()

gemini_api_key = os.getenv("GEMINI_API_KEY")
```

An external provider is then configured:

```python
external_provider = AsyncOpenAI(
    api_key=gemini_api_key,
    base_url="https://generativelanguage.googleapis.com/v1beta/"
)
```

The project sets this client as the default provider for the Agents SDK:

```python
set_default_openai_client(external_provider)
```

---

## 🤖 Agent Configuration

The project creates an agent named **Professor**:

```python
agent = Agent(
    name="Professor",
    instructions="You are good Teaher.",
    model="gemini-2.0-flash"
)
```

The agent receives the following prompt:

```text
hello sir! how are you? Tommorow is my paper you can help me?
```

The response is generated using:

```python
result = await Runner.run(
    agent,
    "hello sir! how are you? Tommorow is my paper you can help me?"
)
```

The final response is displayed with:

```python
print(result.final_output)
```

---

## 🔐 Environment Configuration

The project expects a Gemini API key stored in an environment file.

Create a `.env` file inside the `hello-agent` directory:

```env
GEMINI_API_KEY=your_gemini_api_key
```

### Security

Never commit your actual API key to GitHub.

Add the following to `.gitignore`:

```gitignore
.env
__pycache__/
*.pyc
```

---

## 📋 Prerequisites

Before running the project, make sure you have:

* Python **3.13 or newer**
* Git
* `uv`
* A valid Google Gemini API key

---

## 🚀 Installation


### 1. Navigate to the Project

```bash
cd Agent2-main/hello-agent
```

### 2. Install Dependencies

Using `uv`:

```bash
uv sync
```

---

## ▶️ Run the AI Agent

The project defines two commands in `pyproject.toml`:

```toml
[project.scripts]
hello-agent = "hello_agent:main"
abc = "hello_agent.agent_hello:my_first_agent"
```

### Run the AI Agent

Use:

```bash
uv run abc
```

This executes the `my_first_agent()` function and runs the configured Gemini AI agent.

### Run the Basic Package Command

You can also run:

```bash
uv run hello-agent
```

This command currently prints:

```text
Hello from hello-agent!
```

It does **not** start the AI agent. The actual AI-agent execution is connected to the `abc` command.

---

## ⚙️ Project Configuration

The project's main dependencies are defined in `pyproject.toml`:

```toml
dependencies = [
    "dotenv>=0.9.9",
    "openai-agents>=0.0.14",
]
```

The project uses `uv` for dependency management and Hatchling as its build backend.

---

## 🔄 Gemini as an External Provider

One of the main learning points of this project is configuring the **OpenAI Agents SDK to work with a third-party provider**.

The project creates an `AsyncOpenAI` client using the Gemini API endpoint and then sets it as the default client.

This demonstrates that the Agents SDK can be configured beyond its default provider setup.

---

## 🎯 Learning Objectives

This project demonstrates:

* Creating an AI agent with the OpenAI Agents SDK
* Connecting Gemini as an external AI provider
* Using `AsyncOpenAI`
* Running agents asynchronously with `asyncio`
* Managing API keys with environment variables
* Configuring the Agents SDK API method
* Disabling SDK tracing
* Executing an AI agent from the terminal

---

## 🔮 Future Improvements

Possible improvements for this project include:

* Accepting user input dynamically from the terminal
* Adding conversation history
* Improving agent instructions
* Supporting multiple agents
* Adding streaming responses
* Adding error handling for missing API keys
* Building a web-based interface with Chainlit
* Adding more Gemini model configuration options

---

## 👨‍💻 Author

**Muhammad Zimad**

Data Analyst | AI Agent & Chatbot Developer | Python & Workflow-Automation

GitHub:https://github.com/Muhammad-zimad
