# 0.6 New Note in Single Page App Diagram

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes "Hello" and clicks Save in the SPA

    browser->>server: POST /new_note_spa\nContent: "Hello"
    activate server
    Note right of server: Server saves the new note\nand responds with updated JSON
    server-->>browser: JSON including the new note "Hello"
    deactivate server

    Note right of browser: SPA JavaScript updates the notes list\nwithout reloading the page
```
