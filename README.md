# Agent Development Kit Skills Validation Workshop

This repository contains the Jupyter notebooks for the ADK Skills Validation Workshop.
Each notebook is self-contained, requests secrets only at runtime, and includes a test cell.

## ReadyNow architecture

```mermaid
flowchart TD
    U[User request] --> G[ReadyNow root agent]
    G --> V[Input callback: validation + audit log]
    V -->|weather request| W[Weather specialist]
    V -->|route request| R[Route specialist]
    V -->|current-information request| F[Research / critique / refine workflow]
    W --> GC[Google Maps Geocoding]
    W --> NWS[National Weather Service]
    R --> GD[Google Maps Directions]
    F --> S[Google Search]
    S --> C[Critique]
    C --> X[Refine]
    W --> O[Clear safety response]
    R --> O
    X --> O
    O --> L[Output callback: audit log]
```

## Safety and secret handling

- Google Maps credentials are read from `GOOGLE_MAPS_API_KEY` or requested at runtime.
- No API keys, passwords, tokens, or lab credentials are stored in this repository.
- The ReadyNow agent uses official weather, mapping, and search tools; it tells users to follow official emergency instructions.
