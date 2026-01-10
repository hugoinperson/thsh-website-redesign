# User Stories & Functional Requirements

## 👤 Persona: The "Young Professional" (Potential Member)

- **Story:** As a visitor, I want to see "Upcoming Events" immediately on the homepage so I don't have to hunt for them.
- **Story:** As a visitor, I want to clearly see the price difference between "Member" and "Non-Member" tickets so I understand the value of joining.
- **Story:** As a mobile user, I want the navigation menu to be usable on my iPhone so I can find the address easily.

## 🛡 Persona: The Board Member (Admin)

- **Story:** As an admin, I want to fix a typo on the "About Us" page by clicking a "Edit" button on the visual preview, not by writing code.
- **Story:** As an admin, I want to upload event photos to a "Gallery" without worrying about resizing or optimizing them for the web.
- **Story:** As an admin, I want member renewals to happen automatically via email, rather than me sending manual reminders.

## 🤖 Persona: The System (Automation)

- **Story:** When a user buys a ticket, the system must tag their Neon CRM profile with `Attended: {EventName}`.
- **Story:** If Neon CRM is down, the website should gracefully degrade (show public pricing only) rather than crashing.
