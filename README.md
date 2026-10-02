# Streamy Video Streaming Backend Platform

## Software Technology Course Laboratory Node

* **Student Identity:** [Libihong]
* **Neptun System Code:** [L3UC28]
* **Course Section Reference:** GETAL314-B2a

---

## Workspace Environment Architecture

The diagram below maps out how our development environment connects local code authoring to remote version tracking, using a **Diagrams-as-Code** design pipeline.

```mermaid
flowchart TD
    UserNode["Workstation Client<br>(Terminal CLI / Web Browser)"]
    LiveSandbox["Cloud Sandbox<br>(mermaid.live)"]
    LocalIDE["VS Code IDE<br>(Markdown Preview Extension)"]
    GitStage["Local Git Index<br>(Staging Ledger)"]
    RemoteHub["GitHub Remote Cloud<br>(Streamy Repository Workspace)"]

    UserNode -->|1. Sandbox Syntax| LiveSandbox
    LiveSandbox -->|2. Verified Block Migration| LocalIDE
    LocalIDE -->|3. git add CLI Operations| GitStage
    GitStage -->|4. git push Pipeline Push| RemoteHub
```

---

# Streamy Iterative SDLC Blueprint

The following diagram describes the iterative software development lifecycle used for the Streamy backend platform.

```mermaid
flowchart TD

    subgraph SpecPhase["1. Requirements Specification Block"]
        A["Inception Abstract Created"] --> B["SRS Requirements Compiling"]
    end

    subgraph DesignPhase["2. UML Architectural Modeling"]
        B --> C["Draft System Border Graphs"]
        C --> D["Construct Advanced Class Models"]
    end

    subgraph ValidationGate["3. Verification Gatekeeper Loop"]
        D --> E{"Does Architecture Match Code Specs?"}
        E -->|No: Refactor Blueprint| B
    end

    subgraph ProductionPhase["4. Python Construction Layer"]
        E -->|Yes: Pass Gate| F["Compile Python Class Skeletons"]
        F --> G["Implement Internal Class Logic"]
    end

    subgraph TestingPhase["5. Testing and Verification"]
        G --> H["Execute Unit Tests"]
        H --> I{"Tests Passed?"}
        I -->|No: Fix Implementation| G
    end

    subgraph IntegrationPhase["6. Integration and Repository Layer"]
        I -->|Yes: Pass Tests| J["Run Integration Tests"]
        J --> K["Generate Technical Documentation"]
        K --> L["Git Commit"]
        L --> M["Git Push"]
    end

    subgraph DeploymentPhase["7. Delivery and Maintenance"]
        M --> N["Remote Repository"]
        N --> O["Release / Deployment"]
        O --> P["Maintenance Feedback"]
    end

    P -.->|New Requirements| B

    classDef decisionStyle fill:#f9f,stroke:#333,stroke-width:2px;
    class E,I decisionStyle;
```

---

## System Development Flow

This diagram shows the main progression from requirements to implementation and deployment.

```mermaid
flowchart LR

    Requirements["Requirements<br>Specification"]
    Architecture["UML<br>Architecture"]
    Design["Detailed<br>System Design"]
    Implementation["Python<br>Implementation"]
    Testing["Unit &<br>Integration Testing"]
    Documentation["Technical<br>Documentation"]
    Repository["Git<br>Repository"]
    Deployment["Deployment"]

    Requirements --> Architecture
    Architecture --> Design
    Design --> Implementation
    Implementation --> Testing
    Testing --> Documentation
    Documentation --> Repository
    Repository --> Deployment

    Testing -.->|Defects| Implementation
    Architecture -.->|Architecture Review| Requirements
    Deployment -.->|Maintenance Feedback| Requirements
```

---

## Workspace Development Environment

The development workspace connects the developer, VS Code, Markdown documentation, Mermaid diagrams, Git, and the remote GitHub repository.

```mermaid
flowchart TD

    Developer["Developer"]

    subgraph LocalWorkspace["Local Development Workspace"]

        VSCode["VS Code IDE"]

        Markdown["Markdown Documentation"]

        Mermaid["Mermaid Diagram Blocks"]

        GitRepo["Local Git Repository"]

        WorkingTree["Working Tree"]
        Staging["Staging Area"]
        Commit["Local Commit History"]

    end

    subgraph ExternalTools["External Development Tools"]

        Sandbox["mermaid.live<br>Diagram Sandbox"]

        GitHub["GitHub Remote Repository"]

    end

    Developer --> VSCode

    VSCode --> Markdown
    Markdown --> Mermaid
    Mermaid --> Sandbox

    VSCode --> WorkingTree
    WorkingTree -->|git add| Staging
    Staging -->|git commit| Commit
    Commit -->|git push| GitHub

    GitHub -->|git pull| Commit
```

---

## Git Version Control Pipeline

The following diagram represents the local Git workflow used to synchronize implementation work with the remote repository.

```mermaid
flowchart LR

    WorkingTree["Working Tree"]
    Staging["Staging Area"]
    LocalRepository["Local Repository"]
    RemoteRepository["Remote Repository"]

    WorkingTree -->|git add| Staging
    Staging -->|git commit| LocalRepository
    LocalRepository -->|git push| RemoteRepository

    RemoteRepository -->|git pull| LocalRepository
    LocalRepository -->|checkout / restore| WorkingTree
```

---

## Requirements to Implementation Traceability

This diagram connects the software requirements with architectural design, implementation, and verification activities.

```mermaid
flowchart TD

    Requirement["Software Requirement"]

    SRS["SRS Requirement<br>Specification"]

    UseCase["Use Case<br>Model"]

    ClassModel["UML Class<br>Model"]

    Component["Component<br>Architecture"]

    PythonClass["Python Class<br>Implementation"]

    UnitTest["Unit Test"]

    IntegrationTest["Integration Test"]

    Requirement --> SRS
    SRS --> UseCase
    UseCase --> ClassModel
    ClassModel --> Component
    Component --> PythonClass
    PythonClass --> UnitTest
    UnitTest --> IntegrationTest

    IntegrationTest -.->|Verification Evidence| Requirement
```

---

## Streamy Backend Architecture

The following architecture describes the main logical components of the Streamy video streaming backend.

```mermaid
flowchart TD

    Client["Client Application"]

    APIGateway["API Gateway"]

    Auth["Authentication<br>Service"]

    UserService["User<br>Service"]

    VideoService["Video<br>Service"]

    StreamService["Streaming<br>Service"]

    Storage["Video/Object<br>Storage"]

    Database["Application<br>Database"]

    Logging["Logging &<br>Monitoring"]

    Client --> APIGateway

    APIGateway --> Auth
    APIGateway --> UserService
    APIGateway --> VideoService
    APIGateway --> StreamService

    UserService --> Database
    VideoService --> Database

    VideoService --> Storage
    StreamService --> Storage

    Auth --> Database

    APIGateway --> Logging
    Auth --> Logging
    UserService --> Logging
    VideoService --> Logging
    StreamService --> Logging
```

---

## Iterative Verification Loop

The development process uses verification gates to ensure that the implementation remains consistent with the architecture and requirements.

```mermaid
flowchart TD

    Start["Start Iteration"]

    Requirements["Review Requirements"]

    Architecture["Review UML Architecture"]

    Implementation["Implement Python Code"]

    Verification["Verify Implementation"]

    Decision{"Specification<br>Matches Code?"}

    Refactor["Refactor Architecture<br>or Implementation"]

    Tests["Execute Automated Tests"]

    TestDecision{"All Tests Passed?"}

    Fix["Fix Defects"]

    Commit["Commit Verified Changes"]

    Start --> Requirements
    Requirements --> Architecture
    Architecture --> Implementation
    Implementation --> Verification
    Verification --> Decision

    Decision -->|No| Refactor
    Refactor --> Architecture

    Decision -->|Yes| Tests
    Tests --> TestDecision

    TestDecision -->|No| Fix
    Fix --> Implementation

    TestDecision -->|Yes| Commit

    classDef decisionStyle fill:#f9f,stroke:#333,stroke-width:2px;
    class Decision,TestDecision decisionStyle;
```

---

## Complete Streamy Development Lifecycle

The complete process combines specification, modeling, implementation, testing, version control, and deployment.

```mermaid
flowchart TD

    A["Requirements Specification"]

    B["SRS Documentation"]

    C["UML Use Case Modeling"]

    D["UML Class Modeling"]

    E["Component Architecture"]

    F["Python Class Construction"]

    G["Internal Logic Implementation"]

    H["Unit Testing"]

    I["Integration Testing"]

    J{"Verification Passed?"}

    K["Refactor / Correct"]

    L["Technical Documentation"]

    M["Git Commit"]

    N["Git Push"]

    O["Remote Repository"]

    P["Deployment"]

    Q["Maintenance Feedback"]

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G
    G --> H
    H --> I
    I --> J

    J -->|No| K
    K --> D

    J -->|Yes| L
    L --> M
    M --> N
    N --> O
    O --> P
    P --> Q

    Q -.->|New Requirement| A

    classDef decisionStyle fill:#f9f,stroke:#333,stroke-width:2px;
    class J decisionStyle;
```

---

## Development Commands

The following commands represent the basic local Git workflow.

```bash
git status

git add .

git status

git commit -m "Update Streamy backend architecture and documentation"

git push
```

---

## Repository Synchronization

```mermaid
sequenceDiagram

    participant Developer
    participant LocalGit as Local Git
    participant GitHub as GitHub Remote

    Developer->>LocalGit: Modify source and documentation
    Developer->>LocalGit: git status
    Developer->>LocalGit: git add .
    LocalGit-->>Developer: Changes staged

    Developer->>LocalGit: git commit
    LocalGit-->>Developer: Commit created

    Developer->>GitHub: git push
    GitHub-->>Developer: Remote repository updated
```

---

## Summary

The Streamy development environment follows a **Diagrams-as-Code** workflow in which:

1. Requirements are documented using Markdown.
2. Architecture is represented using Mermaid diagrams.
3. The development environment is managed through VS Code.
4. Python implementation follows the defined architecture.
5. Unit and integration testing provide verification.
6. Git provides local version control.
7. GitHub provides remote repository synchronization.
8. Verification feedback can return the development process to requirements or architectural design.
9. The iterative lifecycle supports continuous refinement of the Streamy backend platform.
