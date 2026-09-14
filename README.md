# 💸 Automated Expense Management & Receipt Processing — n8n Workflow

An automated end-to-end expense processing engine built with n8n. It automatically ingests receipt images/PDFs from Google Drive, parses structured expense data via JSON, screens for duplicate claims, logs clean records into Google Sheets, and dispatches dynamic approval alerts.

---

## ⚙️ What It Does

> 💡 **Workflow Overview**
> 
> * **1. Receipt Ingestion:** Monitors Google Drive for newly uploaded receipt images and PDF invoices.
> * **2. Data Extraction & Cleaning:** Parses text, extracts key fields (Amount, Vendor, Date), and formats raw data into clean JSON.
> * **3. Duplicate Screening:** Queries the master Google Sheet to prevent double-reimbursement of the same receipt.
> * **4. Expense Logging:** Appends verified expense records directly into the central Google Sheets ledger.
> * **5. Dynamic Alert Routing:** Triggers instant approval notifications for high-value expenses and standard logs for routine claims.

---

## 🖼️ System Screenshots

| Workflow Architecture | Receipt Ingestion & Data Extraction |
| :---: | :---: |
| ![n8n Workflow Canvas](Screenshot 2026-09-14 212059.png
Screenshot 2026-09-14 211858.png
Screenshot 2026-09-14 211148.png
Screenshot 2026-09-14 210947.png
Screenshot 2026-09-14 205231.png
Screenshot 2026-09-14 205843.png
) | ![Receipt Data Prep](Screenshot 2026-09-14 212214.png
Screenshot 2026-09-14 211936.png
Screenshot 2026-09-14 211516.png
Screenshot 2026-09-14 210832.png
) |

| Master Expense Ledger |
| :---: |
| ![Google Sheets Expense Database](Screenshot 2026-09-15 001535.png
Screenshot 2026-09-15 001519.png
Screenshot 2026-09-15 001519.png
) |

---

## ⚡ Features & System Capabilities

| Feature | Description |
| :--- | :--- |
| 📥 **Multi-Format Ingestion** | Handles both raw receipt images (PNG/JPG) and PDF invoice documents automatically. |
| 🏷️ **JSON Field Parsing** | Standardizes vendor names, transaction dates, tax values, and total amounts into structured JSON. |
| 🛡️ **Duplicate Claim Guard** | Cross-checks receipt metadata against existing records to flag repeated submissions. |
| 📊 **Centralized Ledger** | Logs every validated claim into Google Sheets with dynamic status tagging. |
| 🚨 **Threshold Alerts** | Routes high-amount expenses to manual review while auto-logging standard claims. |

---

## 📋 Parsed Data Fields

| Field Name | Description | Example Output |
| :--- | :--- | :--- |
| 👤 **Employee Name / ID** | Claim submitter details | `Arsalan Noor (EMP-104)` |
| 🏪 **Vendor Name** | Extracted merchant/store name | `AWS / Uber / Office Depot` |
| 📅 **Transaction Date** | Standardized date string (`YYYY-MM-DD`) | `2026-09-14` |
| 💰 **Total Amount** | Formatted numeric expense total | `$249.50` |
| 🏷️ **Category** | Expense classification | `Software / Travel / Supplies` |
| 📌 **Claim Status** | Decision state | `Approved / Pending Review / Duplicate` |

---

## 🔄 Workflow Execution Pipeline

| Step | Phase | Action / Node Executed | Description |
| :---: | :--- | :--- | :--- |
| **01** | **Ingestion** | `Google Drive Trigger` | Detects new file uploads in the designated Expense Receipts folder. |
| **02** | **Parsing** | `Code Node (JSON Parser)`| Extracts binary text data, formats raw values, and constructs valid JSON objects. |
| **03** | **Deduplication** | `Google Sheets (Lookup)` | Checks existing spreadsheet entries for identical vendor + amount + date matches. |
| **04** | **Routing** | `If / Switch Node` | Evaluates expense threshold limits for instant logging vs approval routing. |
| **05** | **Storage** | `Google Sheets (Append)`| Records clean expense details in the Master Reimbursement Sheet. |
| **06** | **Alerting** | `Gmail / Alert Node` | Sends instant notification emails for flagged or high-value claims. |

---

## 🛠️ Tech Stack & Integration Ecosystem

| Tool / Technology | Role in Workflow |
| :--- | :--- |
| ⚡ **n8n** | Primary workflow orchestration and conditional routing engine |
| 📁 **Google Drive API** | Automated folder polling and file retrieval |
| 📊 **Google Sheets** | Master database for expense reimbursement records |
| 📧 **Gmail API** | Dynamic notification and approval alert dispatching |
| 📜 **JavaScript (ES6+)** | Custom JSON extraction, string formatting, and date sanitization |

---

## 💡 Practical Use Cases

| Business Scenario | Problem Solved | Operational Impact |
| :--- | :--- | :--- |
| **Corporate Travel Reimbursement** | Manual paper receipt processing and slow manual data entry | Reduces expense processing time by ~80% |
| **Finance Team Audit** | Risk of paying double reimbursement for duplicate invoices | 100% automated duplicate prevention before sheet insertion |
| **High-Budget Operations** | Uncontrolled team spending without immediate visibility | Real-time email alerts for any claim exceeding set budget limits |

---

## 🚀 Setup & Execution Guide

| Step | Task | Details |
| :---: | :--- | :--- |
| **01** | **Import Workflow** | Open n8n ➔ Click **Import from file** ➔ Upload `Expense Management Workflow.json`. |
| **02** | **Set OAuth Credentials**| Connect **Google Drive**, **Google Sheets**, and **Gmail** OAuth2 accounts in n8n. |
| **03** | **Link Folder & Sheet** | Set target Google Drive folder ID and Master Expense Sheet ID in node settings. |
| **04** | **Activate System** | Switch workflow toggle to **Active** to start processing incoming receipts in real time. |

---

## 🎬 Live Demo & Walkthrough

> ### 🚀 [▶️ Watch Full Workflow Execution Demo](YOUR_LINKEDIN_LOOM_POST_URL)
> **Platform:** LinkedIn / Loom  
> **What You'll See:** Live file upload to Google Drive ➔ JSON parsing ➔ Duplicate check ➔ Master Sheet insertion ➔ Automated alert generation.

---

## 📜 License

MIT License — Free to use, modify, and deploy for personal or commercial projects.
