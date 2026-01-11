# Project: THSH Digital Transformation (2026)

## Overview

This repository contains the **architecture, planning, and specifications** for the rebuild of the **Taiwanese Heritage Society of Houston (THSH)** website. The project replaces a legacy Weebly/Zeffy/Excel stack with a cloud-native application designed to unify member data and automate administrative tasks.

> [!NOTE]
> This is a **planning and architecture repository only**. No application source code is hosted here. Implementation will be done in a separate repository following these specifications.

## 🎯 Core Objectives

1.  **Unified Member Identity:** Eliminate "disconnected islands." The website must know if a logged-in user is a paid member in **Neon CRM**.
2.  **Dynamic Pricing:** Automatically show discounted event tickets to authenticated members.
3.  **Hands-Off Administration:** Empower non-technical board members to edit content via **Sanity.io** without touching code.
4.  **Mobile-First:** Ensure 100% responsiveness for the 60%+ mobile traffic demographic.

## 🛠 Proposed Tech Stack

| Layer           | Technology                           |
| --------------- | ------------------------------------ |
| Frontend        | Next.js 15 (App Router) + TypeScript |
| Styling         | Tailwind CSS + Shadcn/UI             |
| Backend         | Firebase (Auth, Cloud Functions)     |
| CMS             | Sanity.io (Headless)                 |
| Source of Truth | Neon CRM (via REST API)              |
| AI              | Firebase Genkit (content generation) |

## 📂 Repository Contents

- `architecture.md` — System design and data flow diagrams
- `user_stories.md` — Functional requirements by persona
- `schema.md` — Content model for Sanity CMS
- `current_issues.md` — Prioritized issues with the existing website
- `scoped-features.md` — Features to implement, mapped to issues

## 🚫 Constraints (The "Don'ts")

- **No Zeffy:** We are moving event registration _back_ to Neon CRM to ensure data integrity.
- **No Direct SQL:** All member data access must go through the Neon API proxy (Firebase Functions).
- **No "Hardcoded" Text:** All marketing copy must be fetchable from Sanity CMS.
