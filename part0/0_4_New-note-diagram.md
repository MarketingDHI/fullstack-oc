sequenceDiagram
actor User
participant Browser
participant Server

User->>Browser: Follows the URL https://studies.cs.helsinki.fi/exampleapp/notes
Browser->>Server: HTTP GET Request to https://studies.cs.helsinki.fi/exampleapp/notes
Server-->>Browser: HTML document   
Browser->>Server: HTTP GET Request main.css
Server-->>Browser: .css stylesheet
Browser->>Server: HTTP GET Request main.js
Server-->>Browser: .js file
Browser-->>User: Rendered page

User->>Browser: Writes a note in the input field and presses save button
Browser->>Server: HTTP POST Request to https://studies.cs.helsinki.fi/exampleapp/new_note
Server-->>Browser: HTTP status code 302 - Found
Note left of Server: Forces redirect to address from HTTP header 'Location'
Browser->>Server: HTTP GET Request to https://studies.cs.helsinki.fi/exampleapp/notes
Note left of Browser: Reloads /notes page
Server-->>Browser: HTML document
Browser->>Server: HTTP GET Request main.css
Server-->>Browser: .css stylesheet
Browser->>Server: HTTP GET Request main.js
Server-->>Browser: .js file
Browser-->>User: Rendered page with updated notes list