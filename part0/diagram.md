sequenceDiagram
    actor User 
    participant Browser 
    participant Server 

    User->>Browser: Wpisuje tresc notatki
    User->>Browser: Klika Save
    Note over Browser: Przegladarka wysyla formularz
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate Server
    Note over Server: Serwer zapisuje notatke
    Server-->>Browser: 302 Redirect: /exampleapp/notes
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Server
    Server-->>Browser: 200 - HTML strony z notatkami
    deactivate Server
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>Browser: 304 - CSS z pamieci podrecznej
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    Server-->>Browser: 304 - JavaScript z pamieci podrecznej
    Note over Browser: Skrypt pobiera aktualne notatki
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Server-->>Browser: 200 - JSON z notatkami, w tym nowa notatka
    Note over Browser: Przegladarka wyswietla odswiezona liste
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/favicon.ico
    Server-->>Browser: 404 - brak favicony

