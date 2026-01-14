# 🚘 ApexDrive Bot - Autonomous Dealership Agent

![n8n](https://img.shields.io/badge/Orchestration-n8n-orange?style=for-the-badge)
![OpenAI](https://img.shields.io/badge/AI-OpenAI_GPT4o-blue?style=for-the-badge)
![MongoDB](https://img.shields.io/badge/Database-MongoDB_Atlas-green?style=for-the-badge)
![Docker](https://img.shields.io/badge/Deployment-Docker-blue?style=for-the-badge)

## 📖 Overview
**ApexDrive Bot** is a 24/7 intelligent sales development representative (SDR) capable of managing vehicle inventory queries and autonomously booking test drives. 

Unlike standard chatbots, this agent uses **Retrieval-Augmented Generation (RAG)** to query a live MongoDB database for accurate stock information and performs **Function Calling** to execute real-world actions (booking appointments in Google Sheets and sending HTML email notifications to sales staff).

![System Architecture](https://res.cloudinary.com/dagj9begy/image/upload/v1766418230/1_miqvvv.png)
![Workflow Diagram](https://res.cloudinary.com/dagj9begy/image/upload/v1766418229/2_ykwut6.png)

## 🏗️ Architecture
The system is built on a microservices-inspired architecture using **n8n** workflows:

1.  **Conversational Interface (Telegram):** Handles user intent and natural language processing.
2.  **Inventory Engine (MongoDB):** The "Ground Truth" for vehicle data. The AI queries this before answering to prevent hallucinations.
3.  **Booking Service (Sub-Workflow):** A dedicated logic layer that validates customer data, checks availability, and commits bookings to the CRM (Google Sheets).
4.  **Notification Layer (Gmail):** Dispatches rich HTML lead reports to the sales team immediately upon booking.

## 🚀 Key Features
* **✅ RAG (Retrieval-Augmented Generation):** Connects GPT-4o to a private MongoDB dataset, ensuring the bot only sells cars that actually exist in stock.
* **✅ Agentic Tool Use:** The AI intelligently decides when to "chat" vs. when to "execute tools" (e.g., searching inventory or booking a ride).
* **✅ Strict Data Validation:** Enforces a "5-Point Protocol" (Name, Phone, Date, Time, Vehicle) before allowing a booking to proceed.
* **✅ Omni-Channel Communication:** Receives requests via Telegram and sends business-grade HTML emails to internal teams.

## 🛠️ Tech Stack
* **Orchestration:** n8n (Self-hosted via Docker)
* **LLM:** OpenAI GPT-4o
* **Database:** MongoDB Atlas
* **Integrations:** Telegram Bot API, Google Sheets API, Gmail SMTP
