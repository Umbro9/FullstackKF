sequenceDiagram
    actor User
    participant Browser
    participant Server

    User->>Browser: Wpisuje tresc i klika Save
    Note over Browser: JavaScript przechwytuje formularz
    Note over Browser: Skrypt tworzy notatke i odswieza widok
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa 
    activate Server
    Note over Server: Serwer zapisuje notatke
    Server-->>Browser: 201 - notatka zostala utworzona
    deactivate Server
    Note over Browser: Strona pozostaje otwarta bez przeladowania
