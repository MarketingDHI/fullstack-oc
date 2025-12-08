sequenceDiagram
participant Browser
participant Server

Browser->>Server: HTTP GET Request to https://studies.cs.helsinki.fi/exampleapp/spa
activate Server
Server-->>Browser: HTML document
deactivate Server

activate Browser
Browser->>Server: HTTP GET Request main.css
deactivate Browser
activate Server
Server-->>Browser: .css stylesheet
deactivate Server
activate Browser
Browser->>Server: HTTP GET Request spa.js
deactivate Browser
activate Server
Server-->>Browser: .js file
deactivate Server
activate Browser
Browser->>Server: HTTP GET Request data.json
deactivate Browser
activate Server
Server-->>Browser: .json file
deactivate Server

