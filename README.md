# Streamy Video Streaming Backend Platform 
 
## Software Technology Course Laboratory Node 
*   **Student Identity:** [libinghong] 
*   **Neptun System Code:** [L3UC28] 
*   **Course Section Reference:** GEIAL314-B2a 
 --- 
 
## Workspace Environment Architecture 
The diagram below maps out how our development environment connects local code 
authoring to remote version tracking, using a **Diagrams-as-Code** design pipeline. 
 
```mermaid
flowchart TD
    UserNode["Workstation Client <br> (Terminal CLI / Web Browser)"]
    LiveSandbox["Cloud Sandbox <br> (mermaid.live)"]
    LocalIDE["VS Code IDE <br> (Markdown Preview Extension)"]
    GitStage["Local Git Index <br> (Staging Ledger)"]
    RemoteHub["GitHub Remote Cloud <br> (Streamy Repository Workspace)"]

    UserNode -->|1. Sandbox Syntax| LiveSandbox
    LiveSandbox -->|2. Verified Block Migration| LocalIDE
    LocalIDE -->|3. git add CLI Operations| GitStage
    GitStage -->|4. git push Pipeline Push| RemoteHub

---
title: Streamy Iterative SDLC Blueprint
---
flowchart TD
    subgraph SpecPhase [1. Requirements Specification Block]
        A[Inception Abstract Created] --> B[SRS Requirements Compiling]
    end

    subgraph DesignPhase [2. UML Architectural Modeling]
        B --> C[Draft System Border Graphs]
        C --> D[Construct Advanced Class Models]
    end

    subgraph ValidationGate [3. Verification Gatekeeper Loop]
        D --> E(Does Architecture Match Code Specs?)
        E -->|No: Refactor Blueprint| B
    end

    subgraph ProductionPhase [4. Python Construction Layer]
        E -->|Yes: Pass Gate| F[Compile Python Class Skeletons]
        F --> G[Implement Internal Class Logic]
    end

    E:::decisionStyle
    classDef decisionStyle fill:#f9f,stroke:#333,stroke-width:2px;
