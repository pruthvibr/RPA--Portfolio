# 🌐 Excel-Driven Web Research Robot

## 📋 Project Overview
This UiPath automation acts as an autonomous web research assistant. It is designed to perform bulk data enrichment by reading a target list of entities from an Excel spreadsheet, performing dynamic Google searches in a web browser, scraping the top descriptive results, and compiling the extracted data into a single consolidated report.

## 🛠️ Tech Stack & Skills Demonstrated
* **RPA Platform:** UiPath Studio
* **Core Activities:** Modern Excel Integration (`Use Excel File`, `For Each Excel Row`), UI Browser Automation (`Type Into`, `Get Text`), System IO (`Write Text File`)
* **Techniques:** Dynamic UI Selectors, String Concatenation, Exception Handling (Try-Catch)

## ⚙️ How It Works (The Architecture)

### 1. Excel Data Ingestion
The automation opens a local workbook (`Companies.xlsx`) within an `Excel Process Scope`. It initializes an empty string variable (`allResults`) to act as the master clipboard, and then launches a `For Each Excel Row` loop to process the target list systematically.

<img width="1117" height="2606" alt="Excel web Robot" src="https://github.com/user-attachments/assets/a56c0ecb-aaad-4c77-a914-2b465363e1fa" />

*The complete process architecture showing the Excel loop and web automation sequence.*

### 2. Dynamic Web Automation
For every row in the spreadsheet, the bot opens a new Google Chrome tab. Using dynamic variables, it injects the current company name (`CurrentRow("Name")`) directly into the Google search bar and simulates a keyboard 'Enter' keystroke. 

### 3. Data Scraping & Error Handling
Once the search results load, a `Get Text` activity extracts the target description from the page. This step is wrapped in a robust `Try-Catch` block:
* **Try:** If the UI element is found, the text is extracted and concatenated into the `allResults` variable.
* **Catch (`System.Exception`):** If a network timeout occurs or the UI element fails to load, the bot catches the error, logs a clean "Failed for: [Company Name]" message, and safely proceeds to the next row without terminating the process.

### 4. Output Generation
After the loop successfully processes every row in the spreadsheet, the bot exits the Excel scope and writes the massive compiled string of research data directly into a local `.txt` file using the `Write Text File` activity.

## 🚀 How to Run
1. Clone this repository to your local machine.
2. Open the `Main.xaml` file in UiPath Studio.
3. Place a file named `Companies.xlsx` in your `D:\` drive (or update the file path in the `Use Excel File` activity). Ensure the target data is in a column named "Name".
4. Run the file. The bot will automatically launch Chrome, perform the searches, and generate the final text report.
