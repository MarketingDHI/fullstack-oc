sequenceDiagram
actor User
participant Browser
participant Server

User->>Browser: Follows the URL https://studies.cs.helsinki.fi/exampleapp/spa
Browser->>Server: HTTP GET Request to https://studies.cs.helsinki.fi/exampleapp/spa
Server-->>Browser: HTML document   
Browser->>Server: HTTP GET Request main.css
Server-->>Browser: .css stylesheet
Browser->>Server: HTTP GET Request spa.js
Server-->>Browser: .js file
Browser->>Server: HTTP GET Request data.json
Server-->>Browser: .json file
Browser-->>User: Rendered page

User->>Browser: Writes a note in the input field and presses save button
activate Browser
Browser->>Server: HTTP POST Request to /new_note_spa 
Note right of Browser: Request contains new post date and content as JSON data
Server-->>Browser: HTTP status code 201 - Created
Note left of Browser: Executes JavaScript from .onsubmit() Stays on the page, no reload. 
deactivate Browser
Browser-->>User: Rendered page with updated note list

