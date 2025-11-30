# Sequence Diagram – Creating a New Note ("Hello")

The following diagram illustrates what happens when the user types **"Hello"** into the text field on  
https://studies.cs.helsinki.fi/exampleapp/notes  
and clicks the **Save** button.

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes "Hello" and clicks Save

    browser->>server: POST /new_note\nContent: "Hello"
    activate server
    Note right of server: Server saves the new note\nand responds with a redirect (302) to /notes
    server-->>browser: 302 Redirect /notes
    deactivate server

    Note right of browser: Browser follows the redirect\nand reloads the Notes page

    browser->>server: GET /notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET /main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET /main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: Browser executes main.js

    browser->>server: GET /data.json
    activate server
    server-->>browser: JSON including the new note "Hello"
    deactivate server

    Note right of browser: Browser executes callback\nand renders the notes (including "Hello")
```
