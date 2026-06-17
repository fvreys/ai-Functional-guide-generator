# AI Engineering Graduation Project Template

A starter kit repository for the AI Engineering course's graduation project. Use this repository as a template and build your solution on top of the provided structure. This `README.md` should be modified with the information specific to your application.

You should focus on the "Setup Instructions" section to guarantee that following the instructions from start to finish will allow the application to properly initialize and be ready for use. (Try cloning the repository a few times and go through everything line by line before submitting the final solution). The final solution should be present in the `main` branch only, as other branches will not be reviewed during evaluation.

We strongly recommend using Docker Compose during development (`docker-compose.yml` in this repository is the development version with hot reload for the FastAPI server), and for submitting the solution. If you are also developing a full frontend (e.g., using React), connect both components using Docker Compose.

Initial repository structure:
```
ai-eng-project-template/
├── README.md                    # Main documentation
├── .gitignore                   # Python + IDE + OS ignores
├── .dockerignore                # Files excluded from the Docker build context
├── config.toml                  # Project config
├── pyproject.toml               # Project metadata & dependencies (managed with uv)
├── uv.lock                      # Locked, reproducible dependency versions
├── docker-compose.yml           # Multi-service setup
├── Dockerfile                   # App container
├── .env.example                 # Environment variables template
├── docs/
│   ├── ARCHITECTURE.md          # Architecture write-up template
│   └── SUBMISSION_CHECKLIST.md  # Checklist to run through before submitting
├── src/
│   └── app/
│       ├── __init__.py
│       ├── config.py            # Management for the app settings
│       ├── main.py              # FastAPI app entry point
│       ├── schemas/             # Pydantic models
│       └── services/            # Business logic
└── data/                        # Sample data
```

The application is a simple semantic search engine for movies. It can add movies into the collection and perform semantic search through the existing database. Treat it as a worked example of the intended pattern (FastAPI + Qdrant + an LLM provider) — replace the movie-specific schemas, services, and routes with your own graduation project's domain logic while keeping the same project structure.

## Setup instructions
### Prerequisites

Before running this project, make sure you have the following installed:

- **Docker Engine** - [Installation Guide](https://docs.docker.com/get-docker/)
- **Docker Compose** - [Installation Guide](https://docs.docker.com/compose/install/)

> **Note**: If you're using Docker Desktop, Docker Compose is included automatically.

### Verify Installation
```bash
docker --version
docker compose version 
``` 
### Setup steps   
1. Clone the repository:    
```bash
git clone https://github.com/hyperskill-content/ai-eng-project-template
```
2. Navigate to the project directory:
```bash
cd ai-eng-project-template
```
3. Copy the sample `.env` file and fill it with the required credentials:
```bash
cp .env.example .env
# Add your OpenAI API key to .env
```
4. Build the Docker images and start all services (first time build):
```bash
docker compose up --build
```   
or 
```bash
docker compose up
```
to start the existing pre-built containers.     
5. Go to http://127.0.0.1:8000/docs to interact with the endpoints.

To stop the services and remove volumes (if needed), run  
```bash
docker compose down
# or docker compose down -v to remove the created volumes
```

### Local development without Docker (optional)

Dependencies are managed with [uv](https://docs.astral.sh/uv/), and `uv.lock` pins exact versions so everyone (and CI) resolves the same environment. This is handy for IDE autocompletion, type checking, or running scripts directly, but Docker Compose remains the source of truth for running and submitting the project.

1. [Install uv](https://docs.astral.sh/uv/getting-started/installation/).
2. Install the locked dependencies into a local virtual environment:
```bash
uv sync
```
3. Start Qdrant (the app still needs an instance to talk to; this reuses the same image, port mapping, and storage volume defined in `docker-compose.yml`):
```bash
docker compose up -d qdrant
```
4. Run the app. It's running directly on your machine now, not on the Docker Compose network, so `QDRANT_HOST=qdrant` (the in-network hostname) won't resolve — point it at the host-exposed port from `docker-compose.yml` instead:
```bash
QDRANT_HOST=localhost QDRANT_PORT=6343 uv run uvicorn src.app.main:app --reload
```
5. Add a new dependency:
```bash
uv add <package-name>
```

## Application description and architecture 
Explanations of features, detected areas for improvement, product development plan, and system design of the app should be described in [ARCHITECTURE.md](docs/ARCHITECTURE.md) file.

## Before you submit
Run through the [Submission Checklist](docs/SUBMISSION_CHECKLIST.md) before turning in your project.

## Useful documentation
- [Docker](https://docs.docker.com/) / [Docker Compose](https://docs.docker.com/compose/)
- [uv](https://docs.astral.sh/uv/) — Python dependency & environment management
- [FastAPI](https://fastapi.tiangolo.com/)
- [Pydantic](https://docs.pydantic.dev/)
- [Qdrant](https://qdrant.tech/documentation/)
- [OpenAI API](https://platform.openai.com/docs)
- [The Twelve-Factor App](https://12factor.net/) — good practices for config, env vars, and dependencies
