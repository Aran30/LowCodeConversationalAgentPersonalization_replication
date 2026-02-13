# Demo - Run Instructions

## Requirements
- Docker (Docker Desktop / Docker Engine with Compose support)

## OpenAI key (for personalization features)
Personalization features require an OpenAI API key.

The backend reads it from the `OPENAI_API_KEY` environment variable (wired in `docker-compose.yml`).

You can provide the key in either way:

### Option A (recommended): `.env` file in this folder
Create a file named `.env` inside this `demo` folder with:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

### Option B: set it in your shell before starting
In Git Bash:

```bash
export OPENAI_API_KEY="your_openai_api_key_here"
```

## Start services
From this `demo` folder:

```bash
docker compose up --build
```

This starts:
- BESSER backend on `http://localhost:9000`
- BESSER Web Modeling Editor frontend on `http://localhost:8080`

## Stop services
In the same folder:

```bash
docker compose down
```

## Run agents
You can follow the study instructions to generate a personalized agent.

After generation, multiple files are downloaded in a zip. As described in the instructions, run the file `Agent_Diagram.py`.

Before running `Agent_Diagram.py`, install BESSER Agentic Framework locally:

1. Navigate to [BESSER-AGENTIC-FRAMEWORK](BESSER-AGENTIC-FRAMEWORK).
2. Run:

```bash
pip install .
```

Also make sure to add your OpenAI key to `config.ini` before running the agent.
