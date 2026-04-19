# LogStream Parser 📊

[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![CLI Tool](https://img.shields.io/badge/Type-CLI%20Tool-brightgreen.svg)]()

LogStream Parser is a powerful command-line utility designed to streamline the process of transforming complex, multi-field JSON Lines (JSONL) log files into clean, structured Excel spreadsheets (`.xlsx`).

If you spend time analyzing logs but struggle with nested data and manual parsing, this tool handles the heavy lifting for you. It ensures that critical pieces of information are extracted and presented in a readable table format.

## ✨ Features
*   **Structured Extraction**: Targets specific fields (e.g., `timestamp`, `userType`, `parentUuid`) regardless of where they appear in the JSON structure.
*   **Nested Data Handling**: Safely extracts and serializes content from nested message objects (`message.*`).
*   **CLI Driven**: Operates entirely via command line, making it easy to integrate into pipelines and automation scripts.
*   **Robustness**: Handles missing fields gracefully using default values (empty strings) rather than failing the entire parse job.
*   **Customization**: Supports defining custom output directories and filenames.

## ⚙️ Installation & Prerequisites

This project requires Python 3.8+ and two primary libraries: `pandas` for data handling, and `openpyxl` for writing Excel files.

1.  **Clone the repository:**
    ```bash
    git clone [[your-repo-url]](https://github.com/wh0arey0u777/Claude-Code-JSONL-parser.git)
    cd Claude-Code-JSONL-parser
    ```

2.  **Install Dependencies:**
    ```bash
    pip install pandas openpyxl
    ```

## 🚀 Usage Guide

The script is run from your terminal, providing the source log file and the desired output directory as arguments.

### Basic Command Structure
```bash
python jsonl_to_excel.py <SOURCE_JSONL_PATH> <OUTPUT_DIRECTORY> 
