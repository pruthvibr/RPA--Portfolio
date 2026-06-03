# 🤖 Foundational Web UI Automation Bot

## 📋 Project Overview
This project serves as a foundational demonstration of core Robotic Process Automation (RPA) capabilities using UiPath. It executes a completely autonomous web interaction sequence: launching a browser, simulating human keystrokes to perform a search query, extracting specific data from the resulting web page, and presenting that data back to the user. 

While simple, it establishes the groundwork for modern UI targeting, selector management, and variable assignment.

## 🛠️ Tech Stack & Skills Demonstrated
* **RPA Platform:** UiPath Studio
* **Core Activities:** Web Browser Automation (`Use Application/Browser`), Input Simulation (`Type Into`), Data Extraction (`Get Text`), User Interaction (`Message Box`)
* **Techniques:** Hotkey Injection, UI Element Targeting, String Variable Assignment

## ⚙️ How It Works (The Architecture)

### 1. Browser Initialization
The bot initiates the process by launching a new instance of Google Chrome, ensuring a clean, isolated environment for the automation sequence to run.

<img width="1117" height="779" alt="My first Robot" src="https://github.com/user-attachments/assets/90758beb-7cd5-44f1-84fa-24f65733d205" />

*The complete linear sequence demonstrating basic web interaction and data extraction.*

### 2. Keystroke Simulation & Searching
Using a `Type Into` activity, the bot targets the browser's search/address bar. It inputs a predefined search query ("Ui Path") and seamlessly injects a keyboard hotkey (`[k(enter)]`) to execute the search, perfectly mimicking human interaction.

### 3. Target Extraction
Once the search results load, the bot utilizes a `Get Text` activity. Relying on strict UI selectors, it identifies a specific result container on the page, extracts the inner text, and assigns it to a local string variable (`resultText`).

### 4. User Output
To validate the successful extraction, the sequence concludes by triggering a `Message Box` UI prompt, displaying the scraped data directly to the user's screen.

## 🚀 How to Run
1. Clone this repository to your local machine.
2. Open the `Main.xaml` file in UiPath Studio.
3. Ensure the UiPath Web Automation extension is enabled for Google Chrome.
4. Run the file. The bot will autonomously open Chrome, perform the search, and display a popup box with the extracted text.
