# Content Model (Sanity CMS)

## 📌 Document Type: `event`

- **Title:** String (Required)
- **Slug:** Slug (Auto-generated)
- **Date/Time:** Datetime
- **Location:** String (Default: "Taiwanese Community Center")
- **Main Image:** Image (with hotspot cropping)
- **Pricing:** Object
  - `publicPrice`: Number
  - `memberPrice`: Number
- **Registration Link:** URL (Optional - overrides native flow if needed)
- **Body:** Portable Text (Rich text description)

## 📌 Document Type: `page_home` (Singleton)

- **Hero Section:**
  - Headline: String
  - Subheadline: String
  - Background Image: Image
- **Featured Events:** Array (Reference to `event`)
- **Call to Action:** String (e.g., "Join Today")

## 📌 Document Type: `board_member`

- **Name:** String
- **Role:** String (e.g., "Treasurer")
- **Bio:** Text
- **Photo:** Image
- **Order:** Number (for sorting)
