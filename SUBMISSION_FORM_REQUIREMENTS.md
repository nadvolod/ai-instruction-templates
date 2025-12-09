# LimitlessOS Application Form Requirements

## Overview

A beautiful, fast registration form

---

## User Flow

### 1. Trigger Points
- Primary CTA button in Hero section
- Floating CTA button (appears after scrolling past hero)
- Final CTA section at bottom of page

### 2. Modal Behavior
- Opens as centered modal overlay with backdrop
- Backdrop click closes modal
- Escape key closes modal
- Smooth fade-in animation on open

### 3. Form States

#### Default State
- All fields empty
- Submit button enabled
- Helper text: "We'll reach out soon if you're a fit."

#### Loading State
- Submit button shows loading spinner
- All fields disabled
- Button text: "Submitting..."

#### Success State
- Form fields hidden
- Success icon (checkmark) displayed
- Heading: "Application Received"
- Message: "We review every application personally and will reach out soon if you're a fit."
- "Close" button to dismiss modal

#### Error State
- Error message displayed below form in red
- Form remains editable for retry
- Message: "Something went wrong. Please try again."

---

## Data Storage

### Storage Method
- Vercel Blob Storage
- Single JSON file: `applications.json`
- New submissions appended to existing array

---

## API Endpoints

### POST /api/apply

Submit a new application.

**Request Body:**
\`\`\`json
{
  "name": "string",
  "email": "string",
  "jobTitle": "string",
  "phone": "string (optional)"
}
\`\`\`

**Success Response (200):**
\`\`\`json
{
  "success": true,
  "message": "Application submitted successfully"
}
\`\`\`

**Error Response (500):**
\`\`\`json
{
  "error": "Error message"
}
\`\`\`

### GET /api/apply

Retrieve all applications (for admin use).

**Success Response (200):**
\`\`\`json
{
  "applications": [
    { /* application object */ }
  ],
  "count": 5
}
\`\`\`


---

## Accessibility

- All form fields have associated labels
- Required fields marked with asterisk and aria-required
- Error messages linked to fields via aria-describedby
- Focus trap within modal when open
- Keyboard navigation support (Tab, Escape)
- Loading state announced to screen readers

---

## Visual Design

### Modal Styling
- Border: Subtle border with slight transparency
- Border radius: Rounded corners (lg)
- Max width: 28rem (md)
- Padding: 1.5rem

### Buttons
- Primary (Submit): animated, moving, beautiful and interesting styling effects

---

## Future Enhancements

1. **Email Notifications** - Send confirmation email to applicant
2. **Admin Notifications** - Alert admin of new submissions
3. **Status Management** - Allow admin to update application status
4. **Export Function** - Download applications as CSV
5. **Duplicate Detection** - Prevent same email from applying twice
6. **Rate Limiting** - Prevent spam submissions
7. **CAPTCHA** - Add bot protection
8. **Admin Authentication** - Protect admin dashboard
