# Demo - Run Instructions

## Upstream repositories
This demo contains copied code from the original repositories to preserve the exact example used in the paper.
The upstream projects may evolve over time, so behavior and structure can change in the future.

- https://github.com/BESSER-PEARL/BESSER-Agentic-Framework
- https://github.com/BESSER-PEARL/BESSER
- https://github.com/BESSER-PEARL/BESSER-Web-Modeling-Editor

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
- PostgreSQL database on `localhost:5432` (used later for agents)

## Stop services
In the same folder:

```bash
docker compose down
```

## Run agents
Agent execution requires Python 3.12.

We also provide an already generated personalized agent result (from correctly following the study instructions) in `agent_output/`.
The runnable file is `agent_output/Agent_Diagram.py`.

You can follow the study instructions to generate a personalized agent.

After generation, multiple files are downloaded in a zip. As described in the instructions, run the file `Agent_Diagram.py`.

Before running `Agent_Diagram.py`, install BESSER Agentic Framework locally:

1. Navigate to [BESSER-AGENTIC-FRAMEWORK](BESSER-AGENTIC-FRAMEWORK).
2. Run:

```bash
pip install .
```

Also make sure to add your OpenAI key to `config.ini` before running the agent.

For the provided pre-generated agent in `agent_output/`, `config.ini` already contains the correct database configuration. You only need to add your OpenAI API key.

In addition, adapt the database values in `config.ini` for monitoring and streamlit.
Use the same database credentials as in `docker-compose.yml`:

- `db.monitoring = True`
- `db.monitoring.dialect = postgresql`
- `db.monitoring.host = localhost`
- `db.monitoring.port = 5432`
- `db.monitoring.database = mydatabase`
- `db.monitoring.username = myuser`
- `db.monitoring.password = mysecretpassword`

- `db.streamlit = True`
- `db.streamlit.dialect = postgresql`
- `db.streamlit.host = localhost`
- `db.streamlit.port = 5432`
- `db.streamlit.database = mydatabase`
- `db.streamlit.username = myuser`
- `db.streamlit.password = mysecretpassword`
