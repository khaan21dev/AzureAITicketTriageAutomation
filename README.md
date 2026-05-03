# Azure AI Ticket Triage Automation

**An event-driven, serverless pipeline that automatically classifies incoming support tickets using Azure AI — routing critical issues instantly and eliminating manual triage.**

---

## Project Overview

Support teams waste significant time manually reading, categorising, and escalating tickets. This project automates that process entirely. When a ticket arrives, Azure AI Language analyses the sentiment and content in real time, applies triage logic to determine urgency, and triggers an immediate email alert for critical issues — all without human intervention.

---

## Architecture

**Flow:**
```
Incoming Ticket
      ↓
Azure Function (Node.js) — receives ticket via HTTP trigger
      ↓
Azure AI Language — analyses sentiment and extracts key phrases
      ↓
Triage Logic — classifies as Critical
      ↓
Azure Table Storage — saves ticket data with classification result
      ↓
Logic App (if Critical) — triggers automated email alert immediately
```

**Service breakdown:**

- **Azure Functions (Consumption (Windows) Plan)** — Serverless HTTP endpoint that receives incoming ticket payloads and orchestrates the classification pipeline
- **Azure AI Language (F0)** — Pre-trained AI model performing sentiment analysis and key phrase extraction on ticket text
- **Azure Table Storage** — NoSQL storage persisting every classified ticket with urgency level, sentiment score, and classification result
- **Azure Logic App** — Event-driven workflow triggered when a critical ticket is detected, sending immediate email notification
- **Application Insights** — Live monitoring and logging of all function executions
- **Outlook API Connection** — Authenticated email delivery via Logic App

---

## Project Focus

The focus was designing the end-to-end Azure infrastructure, connecting the services, and ensuring the pipeline works reliably:

- Designed the event-driven architecture and service integration pattern
- Provisioned and configured all Azure resources
- Defined triage logic and classification rules based on real support operations experience
- Configured environment variables, app settings, and secure credential management
- Validated the full pipeline end-to-end including live email delivery

The Node.js function code in `src/functions/classifyTicket.js` was generated using AI tooling based on my architectural specifications. This reflects how modern cloud engineers work — defining what needs to be built and leveraging available tools to implement it efficiently.

---

## Visual Proofs are attached in screenshots folder

---

## Repository Structure

```
├── src/
│   └── functions/
│       └── classifyTicket.js    # HTTP triggered function
├── screenshots/                 # Azure Portal screenshots
├── package.json                 # Node.js dependencies
└── README.md
```

---

## Skills Demonstrated

**Serverless Architecture**
- Azure Functions Consumption Plan pipeline
- HTTP triggers, environment variables, runtime configuration
- Cost optimisation on free tier account

**AI Integration**
- Azure AI Language service integrated into live operational pipeline
- Sentiment analysis applied to real support ticket scenarios
- AI output translated into actionable business logic

**NoSQL Data Storage**
- Azure Table Storage for ticket classification records
- Structured results including sentiment, urgency, and category

**Event-Driven Automation**
- Logic App workflow triggered by ticket urgency classification
- Automated email alerting for critical tickets
- Full automation chain from ticket intake to email delivery proven live

**Secure Configuration**
- All credentials stored as environment variables
- DefaultAzureCredential for passwordless authentication
- OAuth managed connections for API integrations

---

## Business Problem Solved

Support teams handling high ticket volumes face a consistent problem — urgent issues get buried in queues alongside routine requests. Every minute a critical outage sits unescalated costs the business money and damages customer trust.

This system eliminates that delay. Critical tickets are identified and escalated in seconds, not minutes.

---

## Author

Built by Elkhan as part of AZ-104 Microsoft Azure Administrator certification preparation.

