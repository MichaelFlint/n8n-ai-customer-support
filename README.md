# 🚀 AI-Powered Customer Support Automation (Gmail + OpenAI + Slack)

![n8n](https://img.shields.io/badge/n8n-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Gmail](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)
![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)

An intelligent customer support triage and draft generation workflow built in n8n. It classifies incoming emails, queries an internal knowledge base, drafts context-aware responses in Gmail, and escalates dissatisfied customers via Slack alerts in real time.

---

## 🎯 Business Problem

Customer support teams face high ticket volumes, resulting in slow response times, inconsistent answer quality, and burnt-out support agents. Fully automated responses carry risks of AI hallucinations and sending incorrect information to angry customers.

**The Solution:**
This workflow implements a safe **Human-in-the-Loop** architecture:
1. **Automated Triage:** Instantly categorizes inbound support emails and assigns a Sentiment Score (1–5).
2. **Contextual Knowledge Retrieval:** Matches the customer's query against internal knowledge base procedures.
3. **Safe Response Generation:** Creates a polished **Gmail Draft** inside the agent's inbox rather than sending it directly.
4. **Urgent Escalation:** Triggers an immediate Slack notification for critical support cases (Sentiment Score ≤ 2) so agents can prioritize urgent tickets.

---

## 🏗️ Architecture & Data Flow



<img width="2071" height="747" alt="image" src="https://github.com/user-attachments/assets/25e767f8-5998-4f1d-84e6-971d3969aa83" />



## 🛠️ Tech Stack

* **Orchestration:** n8n (Gmail Trigger, Code Node, IF/Switch Nodes, Slack Node)
* **AI Engine:** OpenAI API (`gpt-4o-mini`) with **Structured Outputs / JSON Schema**
* **Integrations:** Gmail API (Thread Management & Drafts), Slack API (Real-time Alerts)
* **Logic & Data Handling:** JavaScript (`Code Node` in n8n for Knowledge Base matching)

---

## ✨ Key Features & Production Readiness

- **Human-in-the-Loop Guardrail:** Eliminates AI hallucination risks by keeping responses in draft mode for support agent review and single-click sending.
- **Structured LLM Triage:** Uses strict JSON Schema enforcement for reliable parsing of email categories, urgency levels, and sentiment scores.
- **Sentiment-Based Escalation:** Automatically flags dissatisfied customers (Sentiment ≤ 2) and sends alerts to Slack with a direct link to the Gmail thread.
- **Thread Context Awareness:** Preserves email headers and conversation threads in Gmail so support interactions remain seamless and continuous.

---

## ⚙️ How to Run / Setup

### Prerequisites
* A running instance of n8n (Cloud or Self-Hosted).
* An active OpenAI API Key.
* OAuth2 connections for **Gmail** and **Slack** in n8n credentials.

### Setup Steps
1. Download the `workflow.json` file from this repository.
2. In your n8n workspace, navigate to: **Workflows** ➔ **Import from File** and select `workflow.json`.
3. Link your Credentials:
   - **OpenAI API Key**
   - **Gmail OAuth2**
   - **Slack OAuth2 / Bot Token**
4. Update the internal Knowledge Base array inside the `Code Node` with your company's support FAQs or policies.
5. Set the Gmail Trigger interval (e.g., check every 2–5 minutes) and activate the workflow.

---

## 👤 Author

**Michał Krzemiński**  
*AI & Automation Developer*  
- LinkedIn: https://www.linkedin.com/in/micha%C5%82-krzemi%C5%84ski-2052b6428/
- GitHub: https://github.com/MichaelFlint
