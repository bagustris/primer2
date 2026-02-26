---
layout: default
title: Mermaid
order: 8
mermaid: true
---

# Mermaid Diagrams

Enable [Mermaid](https://mermaid.js.org/) diagram rendering on any page by adding `mermaid: true` to the front matter:

```yaml
---
layout: default
title: My Page
mermaid: true
---
```

Mermaid is loaded **only on pages that opt in**. Write diagrams using standard fenced code blocks with the `mermaid` language identifier.

## Flowchart

````markdown
```mermaid
flowchart LR
    A[Start] --> B{Is it working?}
    B -- Yes --> C[Great!]
    B -- No  --> D[Debug]
    D --> B
```
````

**Rendered:**

```mermaid
flowchart LR
    A[Start] --> B{Is it working?}
    B -- Yes --> C[Great!]
    B -- No  --> D[Debug]
    D --> B
```

## Sequence diagram

````markdown
```mermaid
sequenceDiagram
    participant Browser
    participant Server
    Browser->>Server: GET /page
    Server-->>Browser: 200 OK + HTML
    Browser->>Server: GET /assets/style.css
    Server-->>Browser: 200 OK + CSS
```
````

**Rendered:**

```mermaid
sequenceDiagram
    participant Browser
    participant Server
    Browser->>Server: GET /page
    Server-->>Browser: 200 OK + HTML
    Browser->>Server: GET /assets/style.css
    Server-->>Browser: 200 OK + CSS
```

## Class diagram

```mermaid
classDiagram
    class Animal {
        +String name
        +makeSound() void
    }
    class Dog {
        +fetch() void
    }
    class Cat {
        +purr() void
    }
    Animal <|-- Dog
    Animal <|-- Cat
```

## Pie chart

```mermaid
pie title Browser Share
    "Chrome"  : 65
    "Firefox" : 15
    "Safari"  : 12
    "Other"   : 8
```
