# 🏋️ AI-Powered Club Management System

An automated Club/Gym Membership Management System built using **n8n, Supabase, JWT Authentication, WhatsApp Automation, Razorpay, and AI**.

The system handles member registration, login, plan activation, payment tracking, and automatic membership reminders without manual intervention.

---

## 🚀 Features

* Member Registration
* JWT Authentication
* Password Hashing with bcrypt
* Membership Status Management
* Plan Activation After Payment
* Razorpay Payment Integration
* WhatsApp Notifications
* AI Generated Membership Summary
* Automatic Expiry Reminders
* Supabase Database Integration

---

## 🛠 Tech Stack

* n8n (Workflow Automation)
* Supabase (PostgreSQL Database)
* JWT Authentication
* bcrypt Password Hashing
* Twilio WhatsApp API
* Razorpay
* Groq AI / Gemini AI
* Webhooks & REST APIs

---

## 📊 Database Structure

### Members Table

| Field         | Description                |
| ------------- | -------------------------- |
| id            | Member ID                  |
| name          | Member Name                |
| email         | Email Address              |
| phone         | Mobile Number              |
| password_hash | Encrypted Password         |
| plan          | Membership Plan            |
| join_date     | Membership Start Date      |
| expiry_date   | Membership Expiry Date     |
| status        | pending / active / expired |

### Plans Table

| Field         | Description   |
| ------------- | ------------- |
| id            | Plan ID       |
| plan_name     | Plan Name     |
| price         | Plan Price    |
| duration_days | Plan Duration |
| features      | Plan Benefits |

### Payments Table

| Field         | Description       |
| ------------- | ----------------- |
| id            | Payment ID        |
| member_id     | Linked Member     |
| amount        | Paid Amount       |
| payment_date  | Payment Date      |
| status        | Payment Status    |
| next_due_date | Next Renewal Date |

---

## 🔄 Workflow 1: Member Registration

POST /registration

Flow:

Webhook → Check Existing User → Password Hashing → Supabase Insert → JWT Token Generation → WhatsApp Welcome Message

---

## 🔐 Workflow 2: Member Login & Dashboard

POST /verify

Flow:

JWT Verify → Fetch Member Data → Check Status

### Active Members

* Membership Details
* Plan Information
* Expiry Date
* AI Summary

### Pending Members

* Available Plans
* Upgrade Information

---

## 💳 Workflow 3: Payment & Plan Activation

PATCH /razor_pay

Flow:

JWT Verify → Fetch User → Create Payment Record → Update Status → Set Join Date → Set Expiry Date → WhatsApp Confirmation

When payment is successful:

* Status changes from Pending → Active
* Join Date is assigned
* Expiry Date is calculated automatically

---

## 🔔 Workflow 4: Automatic Membership Reminder

Daily Scheduled Workflow

Flow:

Schedule Trigger → Fetch Active Members → Check Expiry Date → Send WhatsApp Reminder

Purpose:

* Notify members before membership expiry
* Encourage timely renewal
* Reduce manual follow-ups

---

## 🔒 Security Features

* JWT Authentication
* Password Hashing using bcrypt
* Duplicate Email Prevention
* Status Validation
* Protected Endpoints

---

## 📡 API Endpoints

### Register Member

POST /registration

### Verify Member

POST /verify

### Activate Membership

PATCH /razor_pay

### Daily Reminder

Scheduled Workflow

---

## 📈 Future Enhancements

* Admin Dashboard
* Attendance Tracking
* QR Based Entry System
* Membership Analytics
* Mobile App Integration
* Subscription Auto Renewal

---

## 👨‍💻 Author

Akash Raghuwanshi

Project: Club Management System

Built with n8n, Supabase, JWT, WhatsApp Automation and AI.
