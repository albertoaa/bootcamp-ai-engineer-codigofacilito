# AI Engineer Bootcamp

Base project for the Código Facilito AI Engineer Bootcamp. Integrates with Gemini and Groq APIs for LLM experimentation, token analysis, and streaming comparisons.

## Project Structure

```
bootcamp-ai-engineer-codigofacilito/
├── ai-engineer-bootcamp/
│   ├── main.py                     # CLI demo: chat with LLM, shows usage metrics
│   ├── pyproject.toml              # Project config & dependencies
│   ├── requirements.txt            # Pip dependencies
│   ├── .env.example                # Template for environment variables
│   ├── core/
│   │   ├── config.py               # Loads settings from .env
│   │   ├── llm_client.py           # Gemini LLM client (chat, usage)
│   │   ├── logger.py               # Logging setup
│   │   └── tokenlab.py             # Token counting, latency, streaming, budget
│   └── scripts/
│       ├── streamlit_tokenlab.py   # Streamlit app: streaming vs non-streaming
│       └── practice_tokenlab.py    # CLI practice script (~30 min)
└── outputs/                        # Created at runtime (CSV, charts)
```

## Setup

### 1. Python

Requires **Python 3.10+** (see `pyproject.toml`).

### 2. Virtual Environment

```bash
cd ai-engineer-bootcamp
python3 -m venv venv
source venv/bin/activate   # On macOS/Linux
# On Windows: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
# or
pip install -e .
```

### 4. Environment Variables

Copy the example file and add your API keys:

```bash
cp .env.example .env
```

Edit `.env` and set at least one provider:

**Gemini (default):**
- `GEMINI_API_KEY` — Get from [Google AI Studio](https://aistudio.google.com/apikey)
- `LLM_PROVIDER=gemini`
- `LLM_MODEL` — e.g. `gemini-3-flash-preview` or `gemma-3-27b-it`

**Groq (optional):**
- `GROQ_API_KEY` — Get from [Groq Console](https://console.groq.com/)
- `GROQ_MODEL` — e.g. `llama-3.3-70b-versatile` or `openai/gpt-oss-120b`

## Running the Project

| Command | Description |
|---------|-------------|
| `python main.py` | CLI chat demo (asks for input, prints response + metrics) |
| `streamlit run scripts/streamlit_tokenlab.py` | Streamlit app comparing streaming vs non-streaming |
| `python scripts/practice_tokenlab.py` | Practice script (token comparison, TTFT, budget, temperature) |

## Components

- **`main.py`** — Simple chat using `LLMClient` (Gemini only).
- **`core/tokenlab.py`** — Token counting, latency measurement, streaming, and budget checking for both Gemini and Groq.
- **Streamlit app** — Side-by-side comparison of streaming vs non-streaming responses.
- **Practice script** — Token counts (ES vs EN), TTFT experiments, `BudgetChecker` demo, and temperature experiments; writes to `outputs/`.

## Quick Start

```bash
cd ai-engineer-bootcamp
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
# Edit .env and add GEMINI_API_KEY (or GROQ_API_KEY)
python main.py
```
