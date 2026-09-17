# 🎓 AI College Circular & Grievance Management Agent

### *Automating college communication and student grievance routing with AI-powered n8n workflows.*

> **Logo / Banner Placeholder**
>
> `[Add your project banner or logo here]`

---

## 📌 Badges

![n8n](https://img.shields.io/badge/Automation-n8n-orange)
![AI](https://img.shields.io/badge/AI-Google%20Gemini-blue)
![Google Sheets](https://img.shields.io/badge/Database-Google%20Sheets-green)
![Gmail](https://img.shields.io/badge/Notifications-Gmail-red)
![License](https://img.shields.io/badge/License-MIT-yellow)

> Replace the badge URLs above with your repository-specific build, release, and license badges when CI/CD is configured.

---

## 📖 About the Project

The **AI College Circular & Grievance Management Agent** is an automation system built with **n8n** to streamline communication between college administration, departments, and students.

The system addresses two common college-management challenges:

1. **Distributing circulars to the appropriate departments**
2. **Processing and routing student grievances to the appropriate category**

Instead of manually reading circulars and deciding where they should be sent, administrators can upload a circular PDF. The workflow extracts the document content and uses **Google Gemini** to identify the relevant department and generate a concise summary.

Students can also submit grievances through a dedicated form. The system uses AI to extract the grievance category, summarize the complaint, identify the department, and route the information through the appropriate workflow.

The project also includes a **student registration system** that stores student details and their interests in placements, internships, certifications, workshops, competitions, and hackathons.

---

## 🏗️ System Overview

```text
                         ┌──────────────────────┐
                         │   College Admin      │
                         └──────────┬───────────┘
                                    │
                              Upload PDF
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │   PDF Text Extractor │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │   Google Gemini AI   │
                         │ Information Extractor│
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │ Department Switch    │
                         └──────────┬───────────┘
                                    │
                    ┌───────────────┴───────────────┐
                    │                               │
                    ▼                               ▼
             Department Route                 College-Wide
                    │                               │
                    └───────────────┬───────────────┘
                                    ▼
                              Gmail Notification


Student
   │
   ▼
Grievance Form
   │
   ▼
Google Gemini AI
   │
   ▼
Category + Summary + Department
   │
   ▼
Grievance Switch
   │
   ▼
Gmail Notification
```

---

## 🛠️ Tech Stack

| Technology         | Purpose                                  |
| ------------------ | ---------------------------------------- |
| **n8n**            | Workflow automation and orchestration    |
| **Google Gemini**  | AI-powered information extraction        |
| **n8n Forms**      | Student and administrator input          |
| **Google Sheets**  | Student information storage              |
| **Gmail**          | Automated email notifications            |
| **PDF Extraction** | Extract text from uploaded circular PDFs |

---

## ✨ Core Features

### 📢 AI-Powered Circular Management

* Upload college circulars as PDF files.
* Extract text automatically from uploaded PDFs.
* Use Google Gemini to analyze circular content.
* Identify the intended department.
* Generate a concise circular summary.
* Route circulars using an n8n Switch node.
* Support college-wide circulars using the `ALL` department classification.
* Send processed circular information through Gmail.

Supported department classifications include:

```text
CSE
ECE
EEE
MECH
CIVIL
IT
MBA
ALL
```

---

### 👨‍🎓 Student Registration

Students can register through an n8n form.

The registration workflow collects:

* Full Name
* Student ID
* Email Address
* Department
* Year
* Section

Students can also specify their interest in:

* Placement
* Internship
* Certification
* Workshop
* Competition
* Hackathon

Registration information is stored in Google Sheets.

---

### 📝 Student Grievance Portal

Students can submit grievances using a dedicated form.

The form collects:

* Student Name
* Register Number
* Department
* Year
* Student Email
* Field of Grievance
* Grievance Description

Supported grievance categories include:

```text
Examination
Placement
Administration
Hostel
Laboratory
Transport
Campus
```

---

### 🤖 AI Grievance Processing

Google Gemini processes the submitted grievance and extracts structured information.

The workflow produces:

```text
Category
Summary
Department
```

Example:

```text
Input:

Department: CSE
Field of Grievance: Examination

Grievance Description:
Unable to access my examination results.

Output:

Category: Examination
Summary: Student is unable to access examination results.
Department: CSE
```

---

### 🔀 Automated Routing

n8n Switch nodes route information according to the extracted classification.

```text
                     Input
                       │
                       ▼
                  AI Analysis
                       │
                       ▼
                Classification
                       │
             ┌─────────┴─────────┐
             │                   │
        Circular              Grievance
             │                   │
             ▼                   ▼
      Department Switch     Category Switch
             │                   │
             ▼                   ▼
       Email Workflow       Email Workflow
```

---

### 📧 Email Notifications

The workflow uses Gmail to send notifications after processing.

For grievances, the notification contains:

```text
Category
Summary
Department
```

This provides the recipient with the essential information without requiring them to inspect the original form submission.

---

## 🚀 Getting Started

### Prerequisites

Before importing the workflow, ensure you have:

* An accessible **n8n instance**
* A **Google account** for Gmail and Google Sheets integration
* A configured **Google Gemini API credential**
* Access to a Google Sheet for student registration data

---

## 📥 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

Navigate into the project:

```bash
cd YOUR_REPOSITORY
```

---

### 2. Open n8n

Start or open your n8n instance.

---

### 3. Import the Workflow

In n8n:

```text
Workflows
   ↓
Import from File
   ↓
Agent Ai.json
```

The repository workflow file contains the exported n8n workflow.

---

### 4. Configure Credentials

Reconnect the required integrations inside your n8n instance:

```text
Google Gemini
Google Sheets
Gmail
```

Do **not** commit API keys, OAuth tokens, passwords, or other credentials to GitHub.

---

### 5. Configure Google Sheets

The student registration workflow stores submitted student information in a Google Sheet.

Configure your own spreadsheet and map the required fields.

Expected student information includes:

```text
Full Name
Student ID
Email Address
Department
Year
Section
Placement Interest
Internship Interest
Certification Interest
Workshop Interest
Competition Interest
Hackathon Interest
```

---

## ▶️ Running the Workflow

After importing and configuring the workflow:

1. Activate the workflow where required.
2. Open the student registration form.
3. Submit a test student registration.
4. Verify the data in Google Sheets.
5. Open the circular upload form.
6. Upload a sample PDF circular.
7. Verify AI department extraction.
8. Check the routing workflow.
9. Submit a test grievance.
10. Verify AI grievance classification and email notification.

---

## 🔐 Environment Variables

The current workflow uses n8n-managed credentials rather than explicitly defined environment variables.

If you later move credentials to environment variables, use placeholders such as:

| Variable          | Description                          | Example                |
| ----------------- | ------------------------------------ | ---------------------- |
| `GEMINI_API_KEY`  | Google Gemini API credential         | `YOUR_GEMINI_API_KEY`  |
| `GOOGLE_SHEET_ID` | Student data spreadsheet ID          | `YOUR_GOOGLE_SHEET_ID` |
| `GMAIL_ACCOUNT`   | Gmail account used for notifications | `YOUR_GMAIL_ACCOUNT`   |

### ⚠️ Security

Never commit real credentials:

```env
GEMINI_API_KEY=YOUR_API_KEY
GOOGLE_SHEET_ID=YOUR_SHEET_ID
GMAIL_PASSWORD=YOUR_PASSWORD
```

Add sensitive files to `.gitignore`:

```gitignore
.env
*.key
credentials.json
secrets/
```

---

## 💡 Usage Example

### Circular Processing

An administrator uploads a circular:

```text
CSE students are informed that a technical workshop
will be conducted on the upcoming Friday...
```

The workflow processes the PDF:

```text
PDF Upload
    ↓
Extract Text
    ↓
Google Gemini
    ↓
Department = CSE
Summary = AI-generated summary
    ↓
Switch
    ↓
CSE Route
    ↓
Gmail Notification
```

---

### Grievance Processing

A student submits:

```text
Department: CSE

Field of Grievance: Examination

Grievance Description:
My examination marks are not displayed.
```

The workflow processes the submission:

```text
Grievance Form
      ↓
Information Extractor
      ↓
Category: Examination
Summary: Examination marks are not displayed.
Department: CSE
      ↓
Switch
      ↓
Email Notification
```

---

## 📂 Repository Structure

```text
AI-College-Agent/
│
├── Agent Ai.json
├── README.md
│
└── screenshots/
    ├── circular-workflow.png
    ├── grievance-workflow.png
    ├── student-registration.png
    └── circular-upload.png
```

> The `screenshots/` directory is optional and can be added to document the n8n workflow visually.

---

## 🔄 Workflow Components

The exported workflow contains the following major components:

### Student Registration

```text
On form submission1
        ↓
Append row in sheet
```

### Grievance Processing

```text
On form submission2
        ↓
Information Extractor1
        ↓
Switch1
        ↓
Send a message1
```

### Circular Processing

```text
On form submission
        ↓
Extract from File
        ↓
Information Extractor
        ↓
Switch
        ↓
Merge
        ↓
Send a message
```

The workflow connects Google Gemini models to the information extraction nodes for AI-based processing.

---

## 🤝 Contributing

Contributions are welcome.

### 1. Fork the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

### 2. Create a feature branch

```bash
git checkout -b feature/your-feature
```

### 3. Make your changes

Test the n8n workflow before committing.

### 4. Commit your changes

```bash
git add .
git commit -m "Add your feature"
```

### 5. Push the branch

```bash
git push origin feature/your-feature
```

### 6. Create a Pull Request

Open a Pull Request against the `main` branch and describe:

* What was changed
* Why it was changed
* How it was tested

---

## 🔮 Future Enhancements

Potential extensions for the project include:

* 📱 WhatsApp notifications
* 🔔 Automated event reminders
* 🎯 Personalized opportunity notifications
* 📅 Registration deadline reminders
* 📊 Admin dashboard
* 📈 Grievance analytics
* 🔎 Grievance status tracking
* 📨 Department-specific email routing
* 🤖 Student AI chatbot
* 🔐 Role-based authentication
* 📋 Grievance resolution tracking

---

## 📜 License

This project is licensed under the **MIT License**.

You may add the full MIT license text to a separate `LICENSE` file in the repository.

---

## 👥 Team

This project can be developed collaboratively using GitHub.

Recommended branch structure:

```text
main
│
├── feature/circular-management
├── feature/grievance-system
├── feature/student-registration
└── feature/admin-dashboard
```

Each contributor should work on a separate feature branch and create a Pull Request before merging changes into `main`.

---

## ⭐ Project Summary

**AI College Circular & Grievance Management Agent**

An n8n-based automation system that combines:

```text
       AI
       +
   Automation
       +
 Student Data
       +
Communication
       ↓
College Management Automation
```

Built using **n8n, Google Gemini, Google Sheets, Gmail, and n8n Forms**.
