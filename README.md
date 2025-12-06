
# **ID Card Automation – UiPath (RE-Framework Without Queues)**

This project automates the **ID Card generation process** using **UiPath** built on the **RE-Framework**, but **without using Orchestrator Queues**.
Instead, it uses a **DataTable** as the main data source for transaction processing.

---

## 🚀 **Project Overview**

This automation reads employee/student data from an Excel sheet, processes each row as a transaction, generates an ID card (PDF/Image), and stores the results in an output folder.

The solution uses:

* **Robust RE-Framework structure**
* **DataTable-driven transaction processing**
* **Retry mechanism, exception handling & logging**
* **Configurable settings via Config.xlsx**

---

## 📂 **Project Structure**

```
IDCardAutomation/
│
├── Data/
│   ├── InputData.xlsx        # Employee/Student input records
│   ├── Config.xlsx           # Application settings
│
├── Framework/
│   ├── GetTransactionData.xaml
│   ├── Process.xaml
│   ├── SetTransactionStatus.xaml
│   ├── KillAllProcesses.xaml
│   └── etc...
│
├── Main.xaml
├── Project.json
└── README.md
```

---

## 🧠 **How It Works**

### **1️⃣ Initialization**

* Loads `Config.xlsx`
* Reads the input Excel sheet into a **DataTable**
* Validates required folders and files

### **2️⃣ Transaction Processing**

Each **row** in the DataTable acts as a transaction.
RE-Framework’s internal counter keeps track of the current row.

**Process.xaml performs:**

* Extracts employee data (Name, ID, Dept, etc.)
* Generates ID card format
* Saves output (PDF/Image) to an Output folder

### **3️⃣ Error Handling & Retry**

* System errors → Retries the same transaction
* Business errors → Marks the row as BusinessException and continues

### **4️⃣ Reporting**

* Logs are captured using UiPath’s built-in logging
* Summary report can be generated if needed

---

## ⚙️ **Key Features**

✔ RE-Framework without Orchestrator queues
✔ Processes all transactions using DataTables
✔ Clean architecture and reusable components
✔ Good for beginners learning advanced RPA patterns
✔ Easy to scale and modify

---

## 🛠 **Dependencies**

Make sure your setup includes:

* **UiPath Studio 2022+**
* **Excel dependencies**
* **System, UIAutomation, Mail, PDF packages** (if used)
* **.NET Framework compatible with your UiPath version**

---

## 📘 **Config File Structure**

Sample `Config.xlsx` keys:

| Key            | Value / Description                     |
| -------------- | --------------------------------------- |
| FilePath       | Path to InputData.xlsx                  |
| OutputFolder   | Folder to store generated ID cards      |
| TemplatePath   | Path to ID card template (if used)      |
| MaxRetryNumber | Number of retries for system exceptions |

---

## ▶️ **How to Run**

1. Open the project in UiPath Studio
2. Update paths in `Config.xlsx`
3. Place your input Excel file in `/Data`
4. Run the **Main.xaml**

---

## 📌 **Use Cases**

This project can be adapted for:

* Employee/Student ID card generation
* Badge creation automation
* Membership card automation
* Visitor pass generation

---

## 🤝 **Contributing**

Feel free to fork this repository, raise issues, or submit improvements.

---

## 📄 **License**

This project is open-source under MIT License.

---

