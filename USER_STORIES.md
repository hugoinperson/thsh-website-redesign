# User Stories & Functional Requirements

> _This document captures functional requirements organized by user persona._

## 🎭 Persona Overview

```mermaid
flowchart TB
    subgraph Personas["User Personas"]
        VP["👤 Young Professional<br/>(Potential Member)"]
        BM["🛡️ Board Member<br/>(Admin)"]
        SYS["🤖 System<br/>(Automation)"]
    end

    subgraph Goals["Primary Goals"]
        G1["Discover Events"]
        G2["Understand Value"]
        G3["Manage Content"]
        G4["Automate Tasks"]
    end

    VP --> G1
    VP --> G2
    BM --> G3
    SYS --> G4
```

---

## 👤 Persona: The "Young Professional" (Potential Member)

### User Journey

```mermaid
journey
    title Visitor Event Discovery Journey
    section Landing
      Visit Homepage: 5: Visitor
      See Upcoming Events: 5: Visitor
    section Exploration
      View Event Details: 4: Visitor
      Compare Ticket Prices: 4: Visitor
    section Decision
      Consider Membership: 3: Visitor
      Sign Up or Buy Ticket: 5: Visitor
```

### Stories

| Story                                                                                          | Acceptance Criteria                                         |
| ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| As a visitor, I want to see "Upcoming Events" immediately on the homepage                      | Events section visible above the fold                       |
| As a visitor, I want to clearly see the price difference between Member and Non-Member tickets | Both prices displayed side-by-side with savings highlighted |
| As a mobile user, I want the navigation menu to be usable on my iPhone                         | Hamburger menu, touch-friendly, address easily findable     |

---

## 🛡️ Persona: The Board Member (Admin)

### Content Management Flow

```mermaid
flowchart LR
    A["🔍 Spot Typo/Issue"] --> B["🖱️ Click Edit Button"]
    B --> C["📝 Sanity Studio Opens"]
    C --> D["✏️ Make Changes"]
    D --> E["💾 Publish"]
    E --> F["🔄 Site Revalidates"]
    F --> G["✅ Live on Website"]

    style A fill:#f99,stroke:#333
    style G fill:#9f9,stroke:#333
```

### Stories

| Story                                                                                | Acceptance Criteria                                     |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------- |
| As an admin, I want to fix a typo by clicking an "Edit" button on the visual preview | "Edit in Sanity" button visible when logged in as admin |
| As an admin, I want to upload event photos without worrying about resizing           | Automatic image optimization via Sanity                 |
| As an admin, I want member renewals to happen automatically via email                | Neon CRM automated renewal workflow configured          |

---

## 🤖 Persona: The System (Automation)

### Event Attendance Tagging Flow

```mermaid
sequenceDiagram
    autonumber
    actor User
    participant Web as Website
    participant Pay as Payment
    participant Hook as Webhook
    participant CRM as Neon CRM

    User->>Web: Purchase Ticket
    Web->>Pay: Process Payment
    Pay-->>Hook: Payment Success
    Hook->>CRM: PATCH /accounts/{id}
    Note over CRM: Add tag:<br/>"Attended: {EventName}"
    CRM-->>Hook: 200 OK
```

### Graceful Degradation

```mermaid
stateDiagram-v2
    [*] --> CheckCRM: Page Load
    CheckCRM --> Healthy: CRM Responds
    CheckCRM --> Degraded: Timeout/Error

    Healthy --> ShowDynamic: Member Status Known
    Degraded --> ShowPublic: Fallback Mode

    ShowDynamic --> [*]: Display Member/Public Pricing
    ShowPublic --> [*]: Display Public Pricing Only

    note right of Degraded: Website remains functional
```

### Stories

| Story                                                                 | Acceptance Criteria                                        |
| --------------------------------------------------------------------- | ---------------------------------------------------------- |
| When a user buys a ticket, the system must tag their Neon CRM profile | Webhook fires on payment success, CRM record updated       |
| If Neon CRM is down, the website should gracefully degrade            | Public pricing shown, no error page, user can still browse |
