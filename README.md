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
│   ├── Functional_Guide_Generator_System_Design.pptx    # Presentation of System design
│   ├── LICENSE.md               # License
│   ├── SUBMISSION_CHECKLIST.md  # Checklist to run through before submitting
│   └── System_design.md         # System design
├── src/
│   └── app/
│       ├── __init__.py
│       ├── config.py            # Management for the app settings
│       ├── main.py              # FastAPI app entry point
│       ├── schemas/             # Pydantic models
│       └── services/            # Business logic
└── data/                        # Sample data
```

# Design for a functional guide generator
This design contains:
1. System design
2. Architecture

#  Overview of the application
## 1.1 Problem statement

Writing functional documentation after the implementation of a software feature is rarely done in practice. Developers start working on next tickets, product owners focus on acceptance or the next backlog item — the acquired knowledge embedded in tickets, code, wikis, and demos never makes it into a more functional-oriented manual.

## 1.2 Solution

The Functional Guide Generator aims to generate structured, meaningful, and readable functional documentation based on available information sources, written for persons (not for documentation agents).

## 1.3 Restrictions

- No new information is created. The system assembles and rephrases what is already known and documented.
- Information will not be updated in real time, nor will we have automated interfaces for input of information.
- Documentation is only in English.
- We exclude creation of technical documentation.


## 1.4 Prerequisite for implementation

> Minimal one of the input data streams should contain enough quality information to avoid creating a 'garbage in, garbage out' solution.

#  Other documents
The implementation related files (code, env,..) have not been updated.
