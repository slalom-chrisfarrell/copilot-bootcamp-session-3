# Context Architecture Overview

This repository uses a simple three-part runtime architecture:
- React frontend for user interaction
- Express API for task operations
- In-memory SQLite store for temporary data persistence during runtime

```mermaid
flowchart LR
    U[User]
    FE[React Frontend\npackages/frontend]
    API[Express API\npackages/backend/src/app.js]
    DB[(In-Memory SQLite\n:memory:)]

    U -->|Create, view, edit, complete tasks| FE
    FE -->|HTTP /api/tasks| API
    API -->|SQL queries| DB
    DB -->|Task records| API
    API -->|JSON responses| FE
```

## Sequence: Create TODO

```mermaid
sequenceDiagram
    autonumber
    actor User
    participant FE as React Frontend
    participant API as Express API
    participant DB as In-Memory SQLite

    User->>FE: Enter title/description/due date and submit
    FE->>FE: Validate required title
    FE->>API: POST /api/tasks (JSON payload)
    API->>API: Validate request body
    API->>DB: INSERT INTO tasks (...)
    DB-->>API: New task id
    API->>DB: SELECT * FROM tasks WHERE id = ?
    DB-->>API: Created task row
    API-->>FE: 201 Created + task JSON
    FE-->>User: Show new TODO in task list
```

## Notes
- The backend store is in-memory, so data resets when the server restarts.
- Frontend and backend communicate over REST endpoints under `/api/tasks`.
