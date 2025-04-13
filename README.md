# Investment Portfolio Manager with AI Advisor

## Description

This project is a simple Investment Portfolio Management application built with Python. It allows users to manage a portfolio of securities (stocks and bonds), track their investments in an SQLite database, set risk tolerance levels, calculate overall portfolio risk, and get investment advice using a locally running Ollama AI model. The application features both a Command-Line Interface (CLI) and a Graphical User Interface (GUI).

## Features

* **Buy & Sell Securities:** Add predefined stocks and bonds to your portfolio or sell existing holdings.
* **Database Storage:** Portfolio data is persistently stored using SQLite.
* **Risk Management:**
    * Set a personal risk tolerance level (1-10).
    * Prevent buying securities that exceed the set risk tolerance.
    * Calculate and display the weighted average risk level of the entire portfolio.
* **AI Investment Advice:** Ask investment-related questions and receive advice from a locally hosted Ollama AI model (Mistral).
* **Multiple Interfaces:** Choose between a colorful CLI (using `colorama` and `tabulate`) or a user-friendly GUI (using `tkinter` and `Pillow`).
* **Object-Oriented Design:** Uses classes to model securities, database interactions, AI model communication, controllers, and views.

## Technologies Used

* **Python 3**
* **Standard Libraries:** `sqlite3`, `tkinter`, `json`, `os`, `time`
* **External Libraries:**
    * `requests`: For communicating with the Ollama API.
    * `ollama`: (Note: The `ollamamodel.py` seems to use `requests` directly, but the Ollama Python library might also be intended or useful). Ensure a local Ollama instance is running.
    * `tabulate`: For displaying portfolio data in tables (both CLI and GUI).
    * `Pillow` (PIL Fork): For handling images (logo) in the GUI.
    * `colorama`: For adding color to the CLI output.

## Setup & Installation

1.  **Clone the repository:**
    ```bash
    git clone <github.com/romebechor/StockProject>
    cd <StockProject>
    ```
2.  **Install dependencies:**
    ```bash
    pip install requests tabulate Pillow colorama ollama
    ```
    *(Note: Adjust based on actual library usage, especially regarding `ollama`)*
3.  **Set up Ollama:**
    * Install Ollama from [https://ollama.com/](https://ollama.com/)
    * Ensure the Ollama service is running.
    * Pull the required model (e.g., Mistral):
        ```bash
        ollama pull mistral
        ```
    * Verify the `ollamamodel.py` points to the correct Ollama API endpoint (default is `http://localhost:11434/api/generate`).
4.  **Place Logo:** Ensure the `logo.png` file is in the same directory as the GUI script (`GUIView.py`) or update the path in the script.

## Usage

You can run either the CLI or the GUI version:

* **To run the CLI:**
    ```bash
    python view.py
    ```
    Follow the on-screen menu prompts.

* **To run the GUI:**
    ```bash
    python main_gui.py
    ```
    *(Assuming you have a main script like `main_gui.py` that initializes and runs `GUIView`)*. Example `main_gui.py`:
    ```python
    import tkinter as tk
    from GUIView import GUIView # Assuming GUIView.py contains the GUIView class

    if __name__ == "__main__":
        root = tk.Tk()
        app = GUIView(root)
        root.mainloop()
    ```
    Interact with the application using the buttons.

## Project Structure

* `controller.py`: Handles the main application logic and interactions between models and views.
* `dbmodel.py`: Manages the SQLite database connection and operations (CRUD, risk calculation).
* `securitiesmodel.py`: Defines the classes for different types of securities (Stock, Bond, etc.) and their properties/methods (risk calculation).
* `ollamamodel.py`: Handles communication with the Ollama AI model API.
* `view.py`: Implements the Command-Line Interface (CLI).
* `GUIView.py`: Implements the Graphical User Interface (GUI) using Tkinter.
* `main_gui.py` (Example): Script to launch the GUI application.
* `investments.db`: SQLite database file (will be created automatically).
* `logo.png`: Image file used in the GUI.
