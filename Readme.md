# 🚗 WhatNext Vision Motors – Salesforce Developer Project

## 📌 Overview
This project was developed as part of the **Agentblazer Champion Program** in Salesforce Developer Edition.  
**WhatNext Vision Motors** aims to streamline and automate the vehicle sales process, including managing dealers, customers, orders, test drives, and service requests.  
The solution leverages **custom objects**, **Lightning Apps**, **Flows**, **Apex Triggers**, **Batch Apex**, and **Schedulers** to create a robust automotive management system.

---

## 🎯 Objectives
- Manage complete vehicle lifecycle: sales, orders, test drives, and service requests.
- Automate dealer assignment based on customer location.
- Prevent orders for vehicles that are out of stock.
- Automatically send email reminders for scheduled test drives.
- Bulk-process pending orders and update stock via scheduled jobs.

---

## 🛠️ Technical Stack
- **Platform:** Salesforce Developer Edition
- **Automation:** Flows, Apex Triggers, Batch Apex, Scheduled Jobs
- **UI:** Lightning App with custom tabs
- **Objects:** Custom Salesforce objects with defined relationships

---

## 🗂️ Custom Objects & Relationships

| Object Name | Purpose | Relationships |
|-------------|---------|--------------|
| `Vehicle__c` | Stores vehicle details | Related to Dealer & Orders |
| `Vehicle_Dealer__c` | Stores authorized dealer info | Related to Orders |
| `Vehicle_Customer__c` | Stores customer details | Related to Orders & Test Drives |
| `Vehicle_Order__c` | Tracks vehicle purchases | Related to Customer & Vehicle |
| `Vehicle_Test_Drive__c` | Tracks test drive bookings | Related to Customer & Vehicle |
| `Vehicle_Service_Request__c` | Tracks vehicle servicing requests | Related to Customer & Vehicle |

---

## 🚀 Features Implemented

### 1️⃣ **Custom Tabs & Lightning App**
- Created a **Vehicle** tab for easy navigation.
- Developed a **Lightning App** to access all related objects in one place.

### 2️⃣ **Custom Fields & Relationships**
- Added **Stock Quantity** and other key fields in `Vehicle__c`.
- Lookup relationship from `Vehicle__c` to `Vehicle_Dealer__c`.

### 3️⃣ **Automation with Flows**
- **Nearest Dealer Assignment Flow**: Automatically assigns the nearest dealer to a customer’s order.
- **Test Drive Email Reminder Flow**: Sends automated reminders for scheduled test drives.

### 4️⃣ **Apex Trigger & Handler**
- **Trigger:** `VehicleOrderTrigger`
- **Handler:** `VehicleOrderTriggerHandler`
  - Prevents orders if stock is zero.
  - Decreases stock when an order is confirmed.

### 5️⃣ **Batch Apex Job**
- **Class:** `VehicleOrderBatch`
  - Processes pending orders and confirms them if stock is available.
  - Updates vehicle stock automatically.

### 6️⃣ **Scheduler**
- **Class:** `VehicleOrderBatchScheduler`
  - Runs the batch job at scheduled intervals (e.g., daily at midnight).

---

## 📜 Apex Classes

### `VehicleOrderTriggerHandler`
- **Purpose:** Handles logic for order validation and stock updates.
- **Key Methods:**
  - `preventOrderIfOutOfStock()`
  - `updateStockOnOrderPlacement()`

### `VehicleOrderBatch`
- **Purpose:** Bulk processes all pending orders.
- **Logic:** Confirms orders & updates stock in bulk.

### `VehicleOrderBatchScheduler`
- **Purpose:** Automates batch execution via CRON schedules.

---

## ⚙️ How It Works
1. **Create a Vehicle** → Assign stock quantity.
2. **Customer Places Order** → Trigger checks stock.
3. **Nearest Dealer Flow** assigns dealer automatically.
4. **If Stock Available** → Order is confirmed & stock reduced.
5. **Pending Orders** → Processed via batch job & scheduler.
6. **Test Drive Reminder** → Email sent automatically before scheduled date.

---

## 🎥 Demo Video
[Click here to watch the demo](https://drive.google.com/file/d/1jIiv6QyfvjlYYUVG9WkH6J9FaivBRHaa/view?usp=sharing)

---

## 👨‍💻 Author
**Jitesh Singh**  
BTech CSE | Salesforce Developer | Cybersecurity Enthusiast

---
