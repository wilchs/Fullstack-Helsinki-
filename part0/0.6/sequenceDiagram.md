sequenceDiagram
    participant BROWSER
    participant SERVER

    BROWSER->>+SERVER: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate SERVER
    SERVER-->>+BROWSER: HTML-CODDE
    deactivate SERVER

    BROWSER->>+SERVER: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate SERVER
    SERVER-->>+BROWSER: main.css
    deactivate SERVER

    BROWSER->>+SERVER: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate SERVER
    SERVER-->>+BROWSER: spa.js
    deactivate SERVER
    Note over BROWSER: Obtaining and executing the JavaScript code, where it obtains the JSON data, <br> additionally contains the code to insert a new note <br> and prevents the page from reloading when adding it
    
    BROWSER->>SERVER: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate SERVER
    SERVER-->>BROWSER: [{content: "Hala Madrid", date: "2025-04-17T22:43:36.552Z"}, ... ]
    deactivate SERVER
    Note over BROWSER: The browser renders the data and displays the contents of the JSON

    BROWSER->>SERVER: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate SERVER
    SERVER-->>BROWSER: [{content: "Wilchs desde Chile", date: "2025-04-18T03:32:51.774Z"}] <br> [{message: "note created"}]
    deactivate SERVER
    Note over BROWSER: The browser updates the list without reloading the page
