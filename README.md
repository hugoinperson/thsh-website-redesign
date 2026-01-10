# Project: THSH Digital Transformation (2026)

## Overview

This repository hosts the architecture and source code for the rebuild of the **Taiwanese Heritage Society of Houston (THSH)** website. The project replaces a legacy Weebly/Zeffy/Excel stack with a cloud-native application designed to unify member data and automate administrative tasks.

## 🎯 Core Objectives

1.  **Unified Member Identity:** Eliminate "disconnected islands." The website must know if a logged-in user is a paid member in **Neon CRM**.
2.  **Dynamic Pricing:** Automatically show discounted event tickets to authenticated members.
3.  **Hands-Off Administration:** Empower non-technical board members to edit content via **Sanity.io** without touching code.
4.  **Mobile-First:** Ensure 100% responsiveness for the 60%+ mobile traffic demographic.

## 🛠 Tech Stack

- **Frontend:** Next.js 15 (App Router) + TypeScript
- **Styling:** Tailwind CSS + Shadcn/UI
- **Backend:** Firebase (Auth, Cloud Functions)
- **CMS:** Sanity.io (Headless)
- **Source of Truth:** Neon CRM (via REST API)
- **AI:** Firebase Genkit (for content generation)

## 🚫 Constraints (The "Don'ts")

- **No Zeffy:** We are moving event registration _back_ to Neon CRM to ensure data integrity.
- **No Direct SQL:** All member data access must go through the Neon API proxy (Firebase Functions).
- **No "Hardcoded" Text:** All marketing copy must be fetchable from Sanity CMS.
