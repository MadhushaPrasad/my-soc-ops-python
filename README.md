# 🎯 Soc Ops — Social Bingo

> **Break the ice. Make connections. Win the room.**

A fast, fun Social Bingo web app for in-person mixers and workshops. Find people who match the prompts on your board — get **5 in a row** and shout BINGO! 🎉

[![Python](https://img.shields.io/badge/Python-3.13%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-latest-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![HTMX](https://img.shields.io/badge/HTMX-powered-orange?logo=html5&logoColor=white)](https://htmx.org/)
[![uv](https://img.shields.io/badge/uv-package%20manager-purple)](https://docs.astral.sh/uv/)

---

## ✨ What Is Soc Ops?

Soc Ops turns awkward introductions into a game everyone wants to play. Each player gets a **unique randomised bingo board** filled with prompts like *"has lived in another country"* or *"can juggle"*. Mingle with the crowd, discover who matches each square, mark it off, and race to complete a line!

Built with a lightweight Python/FastAPI backend, server-rendered Jinja2 templates, and zero-JavaScript interactivity via HTMX — the whole app is instant, responsive, and runs from a single command.

### 🃏 How to Play

1. Open the app on any device — no account needed
2. Hit **Start Game** to get your uniquely shuffled board
3. Chat with people around you and mark squares as you find matches
4. Complete a row, column, or diagonal to trigger the **BINGO!** celebration
5. Hit **New Game** whenever you want a fresh board

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | [FastAPI](https://fastapi.tiangolo.com/) + [Uvicorn](https://www.uvicorn.org/) |
| Templating | [Jinja2](https://jinja.palletsprojects.com/) |
| Interactivity | [HTMX](https://htmx.org/) (no page reloads) |
| State | Server-side sessions (cookie-backed) |
| Data validation | [Pydantic v2](https://docs.pydantic.dev/) |
| Package manager | [uv](https://docs.astral.sh/uv/) |
| Language | Python 3.13+ |

---

## 🚀 Quick Start

**Prerequisites:** Python 3.13+, [uv](https://docs.astral.sh/uv/)

```bash
# Install dependencies
uv sync

# Run the dev server
uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

Open **http://localhost:8000** in your browser and you're ready to play!

> 💡 **Using DevContainers?** Open the repo in VS Code and choose *Reopen in Container* — everything is pre-configured for you.

---

## 🧪 Running Tests

```bash
uv run pytest
```

---

## 📚 Workshop Lab Guide

This project is also a **hands-on GitHub Copilot workshop**. Follow the lab guide to transform the app using VS Code Agent Mode step by step:

| Part | Title | Time |
|------|-------|------|
| [**00**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=00-overview) | Overview & Checklist | — |
| [**01**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=01-setup) | Setup & Context Engineering | 15 min |
| [**02**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=02-design) | Design-First Frontend | 15 min |
| [**03**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=03-quiz-master) | Custom Quiz Master | 10 min |
| [**04**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=04-multi-agent) | Multi-Agent Development | 20 min |

> 📝 Lab guides are also available in the [`workshop/`](workshop/) folder for offline reading.

---

## 🤝 Contributing

Contributions are welcome! Check out [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines, and please review our [Code of Conduct](CODE_OF_CONDUCT.md).

---

## 📄 License

This project is licensed under the terms in [LICENSE](LICENSE).
