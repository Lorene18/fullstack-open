# Full Stack Open - Part 0

## 0.4: New note diagram

```mermaid
sequenceDiagram
    ## 0.4: New note diagram

```mermaid
sequenceDiagram
    participant browser
    participant server
    ... (the rest of the diagram)

```

## 0.5: Single page app diagram

```mermaid
sequenceDiagram
    sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```

## 0.6: New note in Single page app diagram

```mermaid
sequenceDiagram
    sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user types a note into the text field and clicks Save

    Note right of browser: The JavaScript event handler prevents the default form submission, creates a new note object, adds it to the notes list and re-renders the notes on the page

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note left of server: The request body is JSON, e.g. { "content": "my new note", "date": "..." }. The server adds the note to its notes array
    server-->>browser: HTTP 201 Created {"message":"note created"}
    deactivate server

    Note right of browser: The browser stays on the same page and does not reload it
```
