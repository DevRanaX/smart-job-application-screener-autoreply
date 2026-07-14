# 🧠 Smart Job Application Screener & Auto-Reply Engine

An enterprise-ready recruitment automation engine designed on **n8n** to streamline candidate screening. The system ingests job applications via a clean frontend form interface, evaluates applicants instantly using **LLMs via Groq**, securely logs candidate records into an **Airtable** central ledger, and applies conditional branch logic to trigger dynamic routing via **Gmail** (dispatching real-time shortlist notifications, internal HR alerts, or polished rejection follow-ups).

---

## 💡 Key Features

* **Structured Applicant Ingestion:** Native **n8n Form Trigger** captures candidate name, email, professional experience (years), technical skill sets, and customized cover letters.
* **Instant AI Fit Scoring:** Uses an isolated **LLM Chain powered by Groq** to evaluate core qualifications against target requirements, outputting an objective numeric scorecard (0-100) instantly without processing latency.
* **Centralized HR Ledger:** Directly logs raw profile strings alongside the dynamic AI score directly into an **Airtable** relational database column mapping layout.
* **Intelligent Conditional Routing:** An **If Node** evaluates whether the AI-Score exceeds a critical hiring threshold (e.g., > 70).
* **Automated Two-Way Notification Logs:** 
  * **High-Score Flow:** Dispatches an immediate high-priority internal alert to the internal HR desk alongside a congratulatory shortlisting confirmation letter to the candidate.
  * **Low-Score Flow:** Politely issues an automated status update email to the candidate, preserving employer branding while minimizing manual administrative overhead.

---

## 🛠️ System Architecture

```text
       [n8n Form Submission]
                 │
         [Basic LLM Chain] <--- (Score Evaluated via Groq)
                 │
        [Airtable: Log Row] 
                 │
          [If Node: Score > 70?]
                 ├───> [TRUE] ───> [Gmail: Send HR Alert] ───> [Gmail: Shortlist Email]
                 │
                 └───> [FALSE] ───> [Gmail: Send Rejection Email]
```
## 📦 How to Deploy

### 1. Prerequisites
* **n8n Instance** (v1.0+ recommended) with active execution capabilities.
* **Airtable Base & Personal Access Token** containing fields mapped precisely to: `Name`, `Email`, `Experience`, `Skills`, `CoverLatter`, and `AI-Score`.
* **Groq API Cloud Key** with explicit model workspace execution capabilities.
* **Gmail Account Integration** authenticated via programmatic OAuth2 web credential profiles.

### 2. Import Workflow
1. **Download** the workspace JSON blueprint file from this repository.
2. **Log into** your central n8n developer workspace dashboard.
3. **Access** the top-right options menu icon and select **Import from File**.
4. **Upload** your downloaded JSON file asset.
5. **Connect** your local saved Airtable, Groq, and Gmail API accounts to their respective node credentials.
6. **Click Save** and toggle the execution active switch to **Active**!

---

## 🧑‍💻 Built With

* **n8n** - Complex Expression Logic & Advanced Conditional Node Architecture.
* **LangChain Integration (n8n Ecosystem)** - Prompt-isolated structural chain infrastructure layers.
* **Groq Cloud API** - Ultra low-latency Large Language Model inference infrastructure.
* **Airtable API** - Relational applicant data persistence ledger.
* **Gmail API** - Programmatic recruitment communications and automated routing engine.
