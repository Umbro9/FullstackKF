sequenceDiagram
    actor User
    participant Browser
    participant Server

    User->>Browser: Otwiera https://studies.cs.helsinki.fi/exampleapp/spa
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    Server-->>Browser: 304 - dokument z pamieci podrecznej
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>Browser: 304 - CSS z pamieci podrecznej
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    Server-->>Browser: 304 - JavaScript z pamieci podrecznej
    Note over Browser: Przegladarka uruchamia skrypt SPA
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Server-->>Browser: 304 - dane z pamieci podrecznej
    Note over Browser: Skrypt pokazuje notatki na stronie
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/favicon.ico
    Server-->>Browser: 404 - brak favicony
