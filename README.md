# Automated Email-Workflow
This is the workflow of Email that customers with different pyment status.
📧 Automated Payment Status Email Workflow (n8n)
📌 Overview

This project is an automated email notification workflow built using n8n.
The workflow reads payment data from Google Sheets, checks payment conditions using Filter and Switch nodes, and sends different email notifications based on the payment status.

It helps schools, academies, freelancers, and small businesses automatically follow up on payments without manual effort.

🧠 Workflow Objective

The goal of this workflow is to:

Monitor payment records automatically

Identify unpaid or overdue payments

Detect incorrect or missing payment data

Send the right email to the right person at the right time

🛠️ Tools & Services Used

n8n (Local Setup)

Google Sheets – payment data source

Filter Node – data validation

Switch Node – decision making

Email (Gmail / SMTP) – notifications

📊 Google Sheets Structure

The workflow reads data from a Google Sheet with the following columns:

Column Name	Description
Name	Customer / Student Name
Email	Recipient Email Address
Amount	Payment Amount
Due_Date	Payment Due Date
Payment_Status	Paid / Unpaid
Invoice_ID	Unique invoice reference
🔄 Step-by-Step Workflow Explanation
🔹 Step 1: Trigger Node

The workflow starts manually or on a schedule (daily / weekly).

This allows automatic checking of payment records.

🔹 Step 2: Google Sheets Node (Read Data)

Fetches rows from the payment sheet.

Each row is processed individually.

Data such as payment status and due date is extracted.

🔹 Step 3: Filter Node (Data Validation)

This node checks:

Email field is not empty

Payment_Status exists

Due_Date is valid

❌ If data is missing or incorrect → sent to Payment Status Error Email

🔹 Step 4: Switch Node (Decision Logic)

The Switch node separates records into three paths:

Case 1️⃣: Unpaid Payments

Condition:

Payment_Status = "Unpaid" AND Due_Date > Today


📨 Email Type: Unpaid Reminder
Purpose:

Polite reminder

Inform customer that payment is pending

Case 2️⃣: Due Date Passed (Overdue)

Condition:

Payment_Status = "Unpaid" AND Due_Date < Today


📨 Email Type: Due Date / Overdue Notice
Purpose:

Urgent tone

Requests immediate payment

Highlights missed deadline

Case 3️⃣: Payment Status Error

Condition:

Payment_Status is empty OR invalid

Due_Date missing

Amount missing

📨 Email Type: Payment Status Error
Purpose:

Alerts admin or customer

Requests correction of records

📧 Email Types Used
📌 1. Unpaid Payment Email

Friendly reminder

Includes name, invoice ID, and amount

Encourages timely payment

📌 2. Due Date / Overdue Email

Professional but urgent

Mentions missed due date

Requests immediate action

📌 3. Payment Status Error Email

Sent when data inconsistency is found

Prevents wrong or misleading emails

Helps maintain clean records

✅ Benefits of This Workflow

⏱ Saves manual follow-ups

📉 Reduces missed payments

🧠 Smart decision-based automation

📧 Personalized communication

📊 Works directly with Google Sheets

🚀 Use Cases

Schools & Academies (fee reminders)

Freelancers (invoice follow-ups)

Small businesses

Subscription services

🔒 Notes

This workflow runs locally on n8n

No sensitive data is stored outside connected services

Fully customizable email templates

📌 Future Improvements

Store email logs in a database

Add WhatsApp or SMS notifications

Generate PDF invoices automatically

Dashboard for payment analytics

🏷️ License

This project is released under the MIT License.
