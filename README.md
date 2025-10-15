# 🇮🇳 Community Embassy Query Automation

> **Automating embassy case reporting for the Indian community in the UAE**
> Built with **Google Forms**, **Google Sheets**, and **Google Apps Script** — powered by **OpenAI GPT-4**.

---

## 🧠 Overview

This project streamlines the process of collecting and forwarding **community member queries** to the **Indian Embassy**.
It uses **Google Forms** to gather details, stores them in **Google Sheets**, and automatically sends **formatted email reports** (with attachments) via **Google Apps Script**.

---

## 🚀 Project Highlights

* ✅ **Automated Data Collection** – via Google Forms
* ✅ **Dynamic Case Classification** – detects and maps case types automatically
* ✅ **AI-Powered Description Polishing** – rewrites reports using GPT-4 for formal tone
* ✅ **Email Routing** – sends to correct embassy (Abu Dhabi / Dubai) dynamically
* ✅ **Attachment Handling** – retrieves files uploaded via Google Drive
* ✅ **Unique Case IDs** – auto-generated for tracking and reporting

---

## ⚙️ Tech Stack

| Component         | Technology                      |
| ----------------- | ------------------------------- |
| Form & Data Input | Google Forms                    |
| Backend Database  | Google Sheets                   |
| Automation Logic  | Google Apps Script (JavaScript) |
| Email Service     | GmailApp API                    |
| AI Integration    | OpenAI GPT-4 API                |
| Documentation     | Markdown, GitHub                |

---

## 📂 Folder Structure

```
google-embassy-query-automation/
│
├── src/
│   └── sendToEmbassy.gs        # Core Google Apps Script logic
│
├── form/
│   └── form_description.md     # Form structure & link
│
├── docs/
│   └── workflow_diagram.png    # Process flow diagram (Form → Sheet → Script → Email)
│
├── .gitignore                  # Ignore temp/system files
└── README.md                   # This documentation file
```

---

## 🧩 How It Works

1. **User fills out the Google Form**
   Community member provides case details, uploads documents, and submits the form.

2. **Form data is stored in Google Sheets**
   Responses are recorded in a structured format.

3. **Apps Script Trigger Executes (`onFormSubmit`)**
   Automatically:

   * Reads form responses
   * Cleans and formats the case details
   * Fetches uploaded files from Drive
   * Sends an email to the relevant embassy

4. **Embassy Receives Structured Email**

   * Email contains all case details and attachments
   * CCs reporter and association president

---

## 🖼️ Workflow Diagram

```mermaid
flowchart TD
  A[Community Member Submits Google Form] --> B[Response stored in Google Sheet]
  B --> C[Apps Script Trigger: onFormSubmit(e)]
  C --> D[Generate Case ID + Format Email]
  D --> E[Send Email via GmailApp]
  E --> F[Embassy Inbox (Abu Dhabi / Dubai)]
  C --> G[Log case details in Sheet]
```

*(You can also replace this with a PNG diagram under `/docs`)*

---

## 🧠 Key Functional Modules

### 🧩 `sendToEmbassy.gs`

Main automation script that:

* Handles form submissions
* Maps case types using `CASE_FIELD_MAP`
* Generates case IDs (e.g., `TFA-151025-DE-001`)
* Formats reports with GPT-4
* Sends embassy and reporter emails with attachments
* Updates the sheet with tracking info

### ⚙️ GPT-4 Integration

The script uses OpenAI API to:

* Convert free-text responses into **formal, diplomatic English**
* Improve readability for embassy staff

*(Note: API key stored securely, not in public repo)*

---

## 📋 Google Form

📍 **Form Link:** [View Live Form](https://forms.gle/d/1yhV21VWVodMthd5QcTWsq5MxPI1fjBAei1szk6gW5Eg)

See `/form/form_description.md` for details on:

* Key form fields
* Example data flow
* Screenshots and field mapping

---

## 🔑 Setup Instructions

### 1️⃣ Configure the Script

* Open your linked Google Sheet → Extensions → Apps Script
* Paste contents of `src/sendToEmbassy.gs`
* Replace with your configuration:

  ```js
  const OPENAI_API_KEY = 'YOUR_API_KEY';
  const EMAIL_ABU_DHABI = 'embassy@domain.com';
  const EMAIL_DUBAI = 'consulate@domain.com';
  ```

### 2️⃣ Set Up Triggers

In Apps Script:

* Click **Triggers (⏰)** → Add Trigger
* Function: `onFormSubmit`
* Event Type: `On Form Submit`

### 3️⃣ Test the Flow

* Submit a sample Google Form response
* Check if the email is received correctly

---

## 🧪 Example Email Output

**Subject:**

```
TFA-151025-DE-001: Death – John Doe
```

**Body:**

> Dear Sir/Madam,
>
> We wish to report the unfortunate death of Mr. John Doe (Passport A1234567) in Abu Dhabi on 10th Oct 2025...
> Supporting documents are attached.
>
> Regards,
> Telangana Friends Association
> +971-551058482

---

## 🧾 Logs & Tracking

Each submission updates tracking columns in Google Sheets:

| Column | Purpose              |
| ------ | -------------------- |
| 99     | Case ID              |
| 100    | Polished GPT summary |
| 101    | Status               |
| 102    | Timestamp            |

---

## 🔒 Security Notes

* API keys are stored privately (not committed to GitHub)
* User emails are only used for communication, not shared
* Sensitive files (Drive uploads) are restricted to authorized users

---

## 🏗️ Future Enhancements

* 📊 Google Data Studio dashboard for case metrics
* 🧾 Auto PDF generation of reports
* 🧠 ChatGPT summary comparison mode
* 📨 Embassy reply integration

---

## 🪪 Author

**👤 Nikhil Reddy**
*Data Engineer | Workflow Automation Enthusiast*


---

## ⚖️ License

MIT License © 2025 Nikhil Reddy
You’re free to use and modify this project with attribution.
