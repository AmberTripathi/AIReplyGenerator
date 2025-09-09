# AI Email Reply Generator for Gmail

![Java](https://img.shields.io/badge/Java-17-orange.svg)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.3.5-brightgreen.svg)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow.svg)
![Platform](https://img.shields.io/badge/Platform-Chrome%20Extension-blue.svg)

A full-stack application that provides an intelligent AI-powered email reply generator directly within the Gmail interface. The project consists of a Java Spring Boot backend that leverages the Google Gemini API and a frontend Chrome Extension that seamlessly integrates with Gmail.

## 🚀 Features

* **Seamless Gmail Integration**: An "AI Reply" button is dynamically added to the Gmail compose toolbar for easy access.
* **Context-Aware Replies**: The extension reads the content of the email you are replying to and sends it to the backend for generating a relevant response.
* **One-Click Generation**: Generate a complete, professional email reply with a single click.
* **Powered by Google Gemini**: Utilizes the state-of-the-art Gemini API for high-quality, natural language text generation.
* **CORS Enabled**: The backend is pre-configured with `@CrossOrigin` to allow requests from the frontend extension.

## 🛠️ Tech Stack

| Component | Technologies Used                                                              |
| :--- |:-------------------------------------------------------------------------------|
| **Backend** | Java 17, Spring Boot 3.3.5, Maven, Spring WebFlux, Project Lombok, Google Gemini API |
| **Frontend** | JavaScript (ES6), HTML5, CSS3 |
| **Platform** | Chrome Extension (Manifest V3) |

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
* **Java Development Kit (JDK) 17** or later
* **Apache Maven**
* A **Google Gemini API Key**
* A Chromium-based browser (e.g., Google Chrome, Brave)

## ⚙️ Setup and Installation

This project has two parts that need to be set up: the **Backend Server** and the **Frontend Chrome Extension**.

### 1. Backend Setup (`AIReplyGeneratorBackend`)

The backend server is responsible for communicating with the Gemini API.

1.  **Clone the repository:**
    ```bash
    git clone <your-repository-url>
    cd <repository-folder>
    ```

2.  **Configure Environment Variables:**
    The application requires your Gemini API key and the API URL. These are loaded from system environment variables to keep them secure.

    Set the following environment variables in your operating system:
    ```bash
    # For Linux/macOS
    export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
    export GEMINI_API_URL="[https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=](https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=)"

    # For Windows (Command Prompt)
    setx GEMINI_API_KEY "YOUR_GEMINI_API_KEY"
    setx GEMINI_API_URL "[https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=](https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=)"
    ```
    *(Note: You may need to restart your terminal or IDE for the changes to take effect.)*

3.  **Run the application:**
    Navigate to the `AI_Reply_generator/AIReplyGeneratorBackend` directory and use the Maven wrapper to start the server.
    ```bash
    # In the AIReplyGeneratorBackend/ directory
    ./mvnw spring-boot:run
    ```
    The server will start on `http://localhost:8080`.

### 2. Frontend Setup (`AIReplyGeneratorChromeExtension`)

The frontend is the Chrome Extension that interacts with the user in Gmail.

1.  **Configure the Backend URL:**
    Open the `AI_Reply_generator/AIReplyGeneratorChromeExtension/content.js` file.
    Find the line with the `fetch` request and replace the placeholder URL with your running backend server's address.

    **Change this line:**
    ```javascript
    const response = await fetch("http://YourBackendRoute" , {
    ```

    **To this:**
    ```javascript
    const response = await fetch("http://localhost:8080/api/email/generate" , {
    ```

2.  **Load the extension in your browser:**
    a. Open your browser and navigate to the extensions management page (e.g., `chrome://extensions` or `brave://extensions`).
    b. Enable **"Developer mode"** with the toggle switch (usually in the top-right corner).
    c. Click the **"Load unpacked"** button.
    d. In the file selection dialog, choose the **`AI_Reply_generator/AIReplyGeneratorChromeExtension`** folder.

## 🚀 Usage

1.  Ensure your backend server is running.
2.  Ensure the Chrome Extension is loaded and enabled in your browser.
3.  Open Gmail and click "Reply" to an email.
4.  The **"AI Reply"** button will appear in the compose window's toolbar.
5.  Click the button. The text will change to "Generating...", and the AI-generated reply will be inserted into the text box automatically.

## 📜 License

This project is licensed under the MIT License. See the `LICENSE` file for more details.
