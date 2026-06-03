# 🤖 Automated Invoice Processing & Data Extraction Bot

## 📋 Project Overview
This enterprise-grade UiPath automation eliminates the manual data entry associated with financial document processing. It autonomously connects to an email server, downloads incoming invoice attachments, extracts semi-structured data from PDFs, and compiles the results into a clean, consolidated financial report.

Designed with robust error-handling, the bot is capable of distinguishing between targeted invoice layouts and incompatible tax documents, ensuring 100% uptime even when encountering dirty data.

## 🛠️ Tech Stack & Skills Demonstrated
* **RPA Platform:** UiPath Studio
* **Core Activities:** IMAP Mail Setup, PDF Text Extraction, System File Management, DataTable manipulation
* **Techniques:** String Manipulation (Splitting/Parsing), Try-Catch Exception Handling, Dynamic Looping, Plain-Text/CSV Data Streams

## ⚙️ How It Works (The Architecture)

### 1. Secure Email Ingestion
The bot establishes a secure IMAP connection to a designated inbox. It identifies unread emails containing invoice attachments and downloads the PDFs directly into a localized processing directory.

<img width="1324" height="3320" alt="(super bot) architecture" src="https://github.com/user-attachments/assets/23e7531e-9caf-4f20-be63-1d41e5d835e1" />

*A high-level view of the workflow architecture, showcasing the linear, multi-stage processing sequence.*

### 2. Intelligent Data Extraction
Using a `For Each File in Folder` loop, the bot reads the raw text of each downloaded PDF. Utilizing precise string manipulation, it isolates the **Invoice Number** and **Total Amount** from the surrounding unstructured text and temporarily stores this data in a virtual DataTable.

<img width="1324" height="3320" alt="Data Extraction" src="https://github.com/user-attachments/assets/469770ec-18f7-4e04-b4c7-8795c43a1f0b" />

*The core extraction engine highlighting PDF reading and variable assignment.*

### 3. Bulletproof Error Handling (Try-Catch)
Real-world data is messy. If the bot encounters a generic tax document or an incompatible layout, the string parsing will fail. Instead of crashing, a `Catch` block intercepts the `System.Exception`. It logs a clean warning message ("Skipping file because it doesn't match our invoice layout") and smoothly commands the loop to process the next file.

<img width="1920" height="1200" alt="Try Catch Excecution" src="https://github.com/user-attachments/assets/0f137617-36f1-480c-8142-2aee588f3045" />

*Output logs proving a flawless 10-second execution run, successfully bypassing 11 incompatible tax documents while extracting valid invoice data.*

### 4. Bypassing System Locks & Generating Output
To ensure absolute reliability and bypass strict Windows OS COM-Interop locks that frequently crash standard Excel activities, the bot utilizes a highly efficient plain-text data stream. It converts the populated DataTable into a comma-separated format and writes it directly to a `.csv` file, resulting in lightning-fast execution and a perfectly formatted final spreadsheet.

<img width="1920" height="1200" alt="Screenshot (408)" src="https://github.com/user-attachments/assets/e74b6680-d3ce-42cf-8501-f2b06b384bec" />

*The final generated CSV report, ready for business use.*

## 🚀 How to Run
1. Clone this repository to your local machine.
2. Open the `Main.xaml` file in UiPath Studio.
3. Update the `Get IMAP Mail Messages` properties with your designated email credentials (use an App Password for Gmail/Outlook).
4. Run the file. The bot will automatically create the required directories, process the emails, and generate `Final_Invoice_Report.csv` in the project folder.
