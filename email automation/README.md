# 📧 Automated Inbox Monitor & Notification Bot

## 📋 Project Overview
This UiPath automation is designed to autonomously monitor an email inbox, extract metadata from incoming messages, and generate execution notifications. By establishing secure IMAP and SMTP connections, the bot eliminates the need to manually check for specific incoming communications, creating a reliable audit log of daily inbox activity.

## 🛠️ Tech Stack & Skills Demonstrated
* **RPA Platform:** UiPath Studio
* **Core Activities:** `Get IMAP Mail Messages`, `Send SMTP Mail Message`, `For Each`, `Assign`
* **Techniques:** Email Object Iteration, Variable Assignment, String Concatenation, Automated Logging & Auditing

## ⚙️ How It Works (The Architecture)

### 1. Secure IMAP Ingestion
The bot establishes a secure connection to the target inbox using the IMAP protocol. It retrieves a batch of recent/unread email messages and stores them as an iterable collection of MailMessage objects.

### 2. Data Iteration & Metadata Extraction
Using a `For Each` loop, the bot systematically processes every single downloaded email. It utilizes `Assign` activities to extract specific properties from the email object—specifically isolating the `Subject` line and converting the `From` address into a readable string.

<img width="1123" height="957" alt="Email automation bot" src="https://github.com/user-attachments/assets/c7d35b6c-428a-4499-91d4-8f99620d0a9f" />

*The core loop extracting sender and subject data from the IMAP collection.*

### 3. Audit Logging
As the bot processes the emails, it uses string concatenation to write a clean, formatted record of every sender and subject directly into the UiPath Output Log (e.g., catching automated alerts from job boards and vendors). This creates a transparent audit trail of the bot's processing history.

<img width="1920" height="1200" alt="Excecution logs" src="https://github.com/user-attachments/assets/535d797c-aa8e-4508-b8d1-b9f72a6e4f49" />

*The output panel showing successful extraction of email metadata and a swift 13-second execution time.*

### 4. Automated SMTP Dispatch
Once the loop is complete and all emails have been parsed and logged, the bot establishes an SMTP connection to dispatch a final notification email. This alerts the user that the automated scraping sequence has finished successfully without requiring them to check the system manually.

## 🚀 How to Run
1. Clone this repository to your local machine.
2. Open the `Main.xaml` file in UiPath Studio.
3. Update the `Get IMAP Mail Messages` properties with your receiving email credentials.
4. Update the `Send SMTP Mail Message` properties with your sending credentials and target notification address.
5. Run the file. The bot will parse the inbox, log the results, and trigger the final notification email.
