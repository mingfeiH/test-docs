# Architecture Overview

This document describes the system architecture.

## Component Diagram

```plantuml
@startuml
skinparam shadowing false

cloud "GitHub" as gh {
  [Webhooks]
  [REST API]
}

rectangle "DocSync App" as app {
  [Webhook Handler]
  [Doc Processor]
  [Confluence Client]
}

cloud "Confluence" as conf {
  [Pages]
  [Attachments]
}

[Webhooks] --> [Webhook Handler]
[Webhook Handler] --> [Doc Processor]
[Doc Processor] --> [REST API] : fetch files
[Doc Processor] --> [Confluence Client]
[Confluence Client] --> [Pages]
[Confluence Client] --> [Attachments]
@enduml
```

## Data Flow

```mermaid
flowchart LR
    A[GitHub Push] --> B[Webhook]
    B --> C[Doc Detector]
    C --> D{File Type?}
    D -->|Markdown| E[MD Converter]
    D -->|AsciiDoc| F[ADoc Converter]
    E --> G[Confluence API]
    F --> G
    G --> H[Published Page]
```

## Key Decisions

- **FastAPI** chosen for async webhook handling
- **SQLite** for local state (delivery dedup, page mappings)
- **Domain-driven design** for clear separation of concerns
