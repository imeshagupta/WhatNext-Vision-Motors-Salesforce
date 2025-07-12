# Salesforce CRM Project – WhatNext Vision Motors: Shaping the Future of Mobility with Innovation and Excellence

This repository contains the Salesforce implementation for **WhatNext Vision Motors**, a next-gen automotive company focused on streamlining vehicle orders, stock validation, and customer engagement through automation and CRM excellence.

---

## 📌 Project Summary

This project aims to transform vehicle ordering, dealer assignment, stock updates, and test drive tracking using Salesforce CRM with a combination of:

- Apex Classes & Triggers  
- Record-Triggered and Scheduled Flows  
- Custom Objects & Relationships  
- Batch Jobs & Scheduled Apex  
- Lightning App with Dynamic Forms  

---

## 🚀 Key Features

- **Auto-assign Dealers** – Assigns nearest dealer based on customer location using Flows  
- **Stock Validation** – Prevents placing orders if vehicle stock = 0 (Apex logic)  
- **Batch Job for Order Processing** – Updates pending orders when stock is replenished  
- **Scheduled Apex** – Runs batch job daily to check & confirm orders  
- **Test Drive Reminders** – Sends email to customer 1 day before scheduled test drive  

---

## 🧰 Tech Stack

- Salesforce Lightning Experience  
- Apex Triggers & Classes  
- Batch Apex  
- Scheduled Apex  
- Record-Triggered Flows  
- Dynamic Lightning Pages & Forms  
- Change Sets for Deployment  

---

## 🧱 Custom Objects

- `Vehicle__c` – Stores vehicle details and stock  
- `Vehicle_Dealer__c` – Authorized dealers and locations  
- `Vehicle_Customer__c` – Customer details  
- `Vehicle_Order__c` – Customer orders  
- `Vehicle_Test_Drive__c` – Test drive scheduling  
- `Vehicle_Service_Request__c` – Service history and maintenance  

_All objects are linked via Lookups or Master-Detail relationships._

---

## 👨‍💻 Apex Development

### Apex Trigger & Handler

- `VehicleOrderTrigger` – Trigger on `Vehicle_Order__c` (before/after insert/update)  
- `VehicleOrderTriggerHandler` – Prevents out-of-stock orders, updates stock on confirmation  

### Batch Apex

- `VehicleOrderBatch` – Confirms pending orders if stock is replenished  
- `VehicleOrderBatchScheduler` – Scheduled Apex to run batch job daily  

---

## 🔄 Flows

### AutoAssignDealer (Record-Triggered Flow)
- Triggers on new Vehicle Order  
- Finds nearest dealer by city  
- Auto-assigns dealer to order  

### TestDriveReminder (Scheduled Flow)
- Runs 1 day before `Test_Drive_Date__c`  
- Fetches customer email  
- Sends reminder email
  
---

## 📄 Project Documentation

A detailed documentation PDF is included in this repository:

👉[WhatNext_Salesforce_Project_Documentaion.pdf](./WhatNext_Salesforce_Project_Documentaion.pdf)

It includes:
- Project goals and architecture
- Custom objects and relationships
- Apex and flow logic
- Screenshots, setup steps, and test cases

---

## 🧪 Manual Execution – Developer Console

To manually schedule the batch job, run this in the Developer Console:

<pre><code>
String cronExp = '0 0 0 * * ?'; // Every day at midnight
System.schedule('Daily Vehicle Order Processing', cronExp, new VehicleOrderBatchScheduler());
</code></pre>
