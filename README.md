# AI Stock Picker Crew

A multi-agent AI system for researching, analyzing, and picking the best stocks in a given sector, powered by [CrewAI](https://crewai.com), Retrieval-Augmented Generation (RAG) memory, and a modern Streamlit dashboard. The system can send push notifications via Pushover and leverages Serper for web search.

---

## Features
- **Multi-agent research workflow**: Agents find trending companies, research them, and pick the best investment.
- **Retrieval-Augmented Memory**: Agents remember facts, entities, and context across runs.
- **Push notifications**: Get instant investment decisions via Pushover.
- **Web search**: Uses Serper for up-to-date news and company trends.
- **Streamlit dashboard**: User-friendly web UI for running and reviewing results.
- **Configurable agents and tasks**: Easily customize via YAML files.

---

## Prerequisites
- Python 3.10–3.13
- [Pushover account](https://pushover.net/) (for notifications)
- [Serper API key](https://serper.dev/) (for web search)
- (Optional) OpenAI or Gemini API key if using LLMs that require them

---

## Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd stockpicker_!
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

---

## Configuration

### 1. **Environment Variables**
Create a `.env` file in the project root with the following (replace with your actual keys):

```
PUSHOVER_USER=your_pushover_user_key
PUSHOVER_TOKEN=your_pushover_app_token
SERPER_API_KEY=your_serper_api_key
OPENAI_API_KEY=your_openai_api_key   # if using OpenAI
GEMINI_API_KEY=your_gemini_api_key   # if using Gemini
```

### 2. **Agent and Task Configuration**
- Edit `src/stockpicker/config/agents.yaml` to define agent roles, goals, and LLMs.
- Edit `src/stockpicker/config/tasks.yaml` to define the workflow and outputs.

---

## Usage

### **A. Command Line**

```bash
python -m src.stockpicker.main
```

### **B. Streamlit Dashboard**
Launch the web UI:
```bash
streamlit run app.py
```
- Select a sector and date
- Click "Run Stock Picker"
- View results, download reports, and see backend logs in the UI

---

## Outputs
- `output/decision.md` — Final investment decision and rationale
- `output/research_report.json` — Detailed research on trending companies
- `output/trending_companies.json` — List of trending companies found

---

## Notifications
- When the best company is picked, a push notification is sent to your device via Pushover (if credentials are set).

---

## Customization
- **Add new agents or tasks**: Edit the YAML files in `src/stockpicker/config/`.
- **Add new tools**: Place Python modules in `src/stockpicker/tools/` and reference them in agent configs.
- **Change memory settings**: Adjust memory configuration in `src/stockpicker/crew.py`.

---

## Troubleshooting
- **No notification received?**
  - Check your `.env` for correct Pushover keys.
  - Ensure your device is registered with Pushover.
- **Web search not working?**
  - Check your Serper API key and quota.
- **LLM errors or empty responses?**
  - Ensure your LLM API key is set and valid.
  - Check for rate limits or quota exhaustion.
- **Memory errors (RAG/SQLite)?**
  - Ensure the `memory/` directory exists and is writable.
  - Check that all URLs in config files start with `http://` or `https://` if required.
- **General debugging**
  - Use the Streamlit UI's "Show backend logs" to see all print output and errors from the backend.



---

## Credits
- [CrewAI](https://crewai.com)
- [Serper](https://serper.dev/)
- [Pushover](https://pushover.net/)
- [Streamlit](https://streamlit.io/)
