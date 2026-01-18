# Extractor
# Firebase Document Approval Dashboard

A **frontend-only document approval system** built using **HTML, CSS, JavaScript, and Firebase services**, created as part of an **SDE Internship Assignment**.

The app allows a writer to upload a document, automatically extract its contents, and submit it for manager approval. The manager is notified via email and can approve or reject the submission using secure links.

---

## 🧩 Problem Overview

Build a tiny service that:
- Accepts document uploads from a writer
- Extracts **title, body, and optional image reference**
- Submits the document for **manager approval**
- Sends an **email notification with approve/reject links**
- Updates approval status in real time

All functionality is implemented **without a traditional backend server**, using **Firebase**.

---

## ✨ Features

### 1. Document Upload & Parsing
- Supported formats:
  - `.docx`
  - `.txt`
  - `.md`
- Parsing rules:
  - **First line** → Title
  - **Remaining content** → Body
  - If the first line matches:
    - `![caption](image.png)`  
    - or an image URL  
    it is treated as an **optional image reference**
- Handles edge cases:
  - Empty files
  - Missing title
  - Invalid file types

---

### 2. Authentication & Access Control
- Firebase Authentication
- Two roles:
  - **Writer** – upload & submit documents
  - **Manager** – approve or reject submissions
- Only authenticated users can access the dashboard

---

### 3. Submission Workflow
- Writer clicks **“Submit for Approval”**
- Submission states stored in Firestore:
  - `draft`
  - `pending`
  - `approved`
  - `rejected`
- Status updates are reflected instantly in the UI

---

### 4. Email Notification (Firebase)
- On submission:
  - Email sent via **Firebase Email / Gmail SMTP setup**
  - Email includes:
    - Document title
    - First 100 characters of content
    - Approve & Reject links
- Clicking a link:
  - Updates approval status in Firestore
  - Returns a simple confirmation message

---

### 5. Manager Approval (No Separate Dashboard)
- No dedicated manager UI required
- Approval handled via:
  - Email action links
  - Optional minimal status confirmation page

---

## 🛠 Tech Stack

- **Frontend:** HTML, CSS, Vanilla JavaScript
- **Authentication:** Firebase Auth
- **Database:** Firebase Firestore
- **Email:** Firebase + Gmail SMTP
- **Hosting:** Firebase Hosting

---

## 🚀 Setup Instructions

1. Clone the repository
   ```bash
   git clone <repo-url>
   cd firebase-document-approval
