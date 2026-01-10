# System Architecture

## 🏗 High-Level Design

The system follows a **Hybrid Headless** architecture. The frontend is decoupled from the content (Sanity) and the business logic (Neon CRM).

### The "Bridge" Pattern (Member Verification)

We do not duplicate the Neon database. We verify against it.

1.  **User Login:** User signs in via Firebase Auth (Google/Email).
2.  **Claim Enrichment (On Call):**
    - Frontend calls Firebase Cloud Function: `verifyMembership()`.
    - Function queries Neon CRM API: `GET /accounts?email={user.email}`.
    - **Logic:**
      - IF `enrollment_status === 'Active'`: Return `{ isMember: true }`.
      - ELSE: Return `{ isMember: false }`.
3.  **UI Update:** Client receives status and switches UI mode (e.g., "Member Price: $10").

## 🔄 Data Flow Diagrams

### 1. Content Rendering (Static/Revalidated)

`Sanity Studio` (Board Edits) -> `Sanity Content Lake` -> `Next.js Build/Revalidate` -> `Public Website`

### 2. Event Registration (Dynamic)

`User` -> `Event Page` -> `Select Ticket` -> `Stripe/Neon Pay` -> `Neon CRM Webhook` -> `Update Member Record`

## 🔐 Security Models

- **Neon API Keys:** Stored strictly in Firebase Secret Manager. NEVER exposed to client.
- **CMS Access:** Role-based access within Sanity (Editor vs. Admin).
