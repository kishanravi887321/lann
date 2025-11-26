# Time Table Management System Diagrams

Here are the simple UML diagrams for a Time Table Management System using Mermaid syntax. You can view these diagrams by opening the VS Code Preview (Ctrl+Shift+V).

## 1. Use Case Diagram
Shows the interactions between users (Actors) and the system.

```mermaid
usecaseDiagram
    actor Admin
    actor Teacher
    actor Student

    package "Time Table System" {
        usecase "Create Timetable" as UC1
        usecase "View Timetable" as UC2
    }

    Admin --> UC1
    Admin --> UC2
    Teacher --> UC2
    Student --> UC2
```

## 2. Class Diagram
Shows the structure of the system, classes, and their relationships.

```mermaid
classDiagram
    class User {
        +String name
        +String role
        +login()
    }

    class Admin {
        +createTimetable()
    }

    class Timetable {
        +String classId
        +show()
    }

    class Course {
        +String name
        +String time
    }

    User <|-- Admin
    Admin --> Timetable : manages
    Timetable "1" *-- "*" Course : contains
```

## 3. Activity Diagram
Shows the flow of creating a timetable (Admin workflow).

```mermaid
flowchart TD
    Start([Start]) --> Login[Admin Login]
    Login --> Input[Enter Course & Time]
    Input --> Check{Slot Free?}
    Check -- Yes --> Save[Save Timetable]
    Check -- No --> Error[Show Error]
    Save --> Stop([Stop])
    Error --> Input
```

## 4. Sequence Diagram
Shows the sequence of messages when a user views a timetable.

```mermaid
sequenceDiagram
    participant User
    participant System
    participant Database

    User->>System: Request Timetable
    System->>Database: Query Data
    Database-->>System: Return Timetable Data
    System-->>User: Display Timetable
```
