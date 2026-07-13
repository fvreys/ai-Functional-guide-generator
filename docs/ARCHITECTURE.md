For this architecture overview, check also the System design under chapter 3. 

# Functional Guide Generator — Architecture Diagram

## System Architecture

```mermaid
flowchart LR
  subgraph SRC["Input sources"]
    I1["Requirements &\nspecifications"]:::grey
    I2["Features &\nuser stories"]:::blue
    I3["Application\nscreenshots"]:::grey
    I4["Demo meeting notes\n& recordings"]:::grey
    I5["Code repository"]:::grey
  end

  subgraph L1["Layer 1 — Ingest & preprocess"]
    direction TB
    A1[Ingest]:::amber --> A2[Preprocess]:::amber --> A3[Embed & store]:::amber
  end

  subgraph L2["Layer 2 — Retrieve & generate"]
    direction TB
    B1[Retrieve]:::amber --> B2[Generate]:::amber
  end

  subgraph L3["Layer 3 — Evaluate & serve"]
    direction TB
    C1[Evaluate]:::amber --> C2[Serve]:::amber
  end

  MD["Markdown\n(default)"]:::green

  subgraph POST["Post-processing"]
    P1[Word]:::green
    P2[PDF]:::green
    P3[HTML]:::green
    P4[Wiki page]:::green
  end

  I1 & I2 & I3 & I4 & I5 --> L1
  L1 --> L2
  L2 --> L3
  L3 --> MD
  MD --> P1 & P2 & P3 & P4

  classDef blue  fill:#E6F1FB,stroke:#378ADD,color:#0C447C
  classDef grey  fill:#F5F5F5,stroke:#999999,color:#666666
  classDef amber fill:#FAEEDA,stroke:#BA7517,color:#633806
  classDef green fill:#EAF3DE,stroke:#639922,color:#27500A
```

## Architecture Overview

### Input Sources

**Primary input source (active):**
- **Features & user stories** — Agile board items (Jira, Azure DevOps)

**Future input sources (greyed out):**
- Requirements & specifications (wiki, documents, product backlog)
- Application screenshots
- Demo meeting notes & recordings
- Code repository (GitHub, etc.)

### Processing Layers

1. **Layer 1 — Ingest & Preprocess**
   - Ingest: fetch raw artifacts from source systems
   - Preprocess: clean, validate, and chunk text
   - Embed & store: convert chunks to vectors and store with metadata

2. **Layer 2 — Retrieve & Generate**
   - Retrieve: semantic search to fetch relevant chunks
   - Generate: LLM synthesis into functional documentation

3. **Layer 3 — Evaluate & Serve**
   - Evaluate: quality scoring via LLM-as-judge and manual review
   - Serve: deliver final documentation

### Output Formats

**Default:** Markdown

**Post-processing options:**
- Word
- PDF
- HTML
- Wiki page
