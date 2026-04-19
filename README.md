# LogStream Parser 📊

[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![CLI Tool](https://img.shields.io/badge/Type-CLI%20Tool-brightgreen.svg)]()

This Parser is a command-line utility designed to streamline the process of transforming Claude Code multi-field JSON Lines (JSONL) log files into clean, structured Excel spreadsheets (`.xlsx`).


## ⚙️ Installation & Prerequisites

This project requires Python 3.8+ and two primary libraries: `pandas` for data handling, and `openpyxl` for writing Excel files.

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/wh0arey0u777/Claude-Code-JSONL-parser.git
    cd logstream-parser
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
```

### Example 1: Standard Run
To parse a log file named `session.jsonl` and save the output in a new folder called `analysis_reports`:

```bash
python jsonl_to_excel.py ./data/session.jsonl ./output_logs
```

### Example 2: Custom Output Name
If you want to specify a different name for the Excel file (e.g., for daily runs):

```bash
python jsonl_to_excel.py ./archive/log_batch.jsonl ./results --output-name log_2024_report.xlsx
```

### 📝 Example Execution Walkthrough
If you run: `python jsonl_to_excel.py aed8b7bc-06ab-4495-a404-9474476a188b.jsonl ./output`

The script will create the `./output` directory (if it doesn't exist) and generate `claude_session_log.xlsx` inside it, containing all the structured data.

## 🧬 Technical Deep Dive
### Field Mapping
The script specifically extracts the following fields from each JSONL entry:

| Column Name | Source Key / Logic | Description | Example Data Type |
| :--- | :--- | :--- | :--- |
| `timestamp` | `data['timestamp']` | Time of event occurrence. | Date/Time String |
| `type` | `data['type']` | The primary type of log entry (e.g., `system`, `user`). | String |
| `parentUuid` | `data['parentUuid']` | UUID linking this entry to a parent action. | UUID/Null |
| `message.role` | `data['message']['role']` | The role of the message (e.g., `user`, `assistant`). | String |
| `message.content` | `data['message']['content']` | The main body content of the message. | Text/JSON String |
| `promptId` | `data['promptId']` | ID associated with the prompt or request. | UUID/Null |
| `permissionMode` | `data['permissionMode']` | Access mode used for the operation. | String |
| `userType` | `data['userType']` | The source user type (e.g., `external`). | String |
| `entryPoint` | `data['entrypoint']` | The entry point of the command (mapped from JSON's lowercase `entrypoint`). | String |
| `cwd` | `data['cwd']` | Current working directory path. | File Path String |

### ⚠️ Notes on Data Integrity
*   **JSONL Format**: The tool expects a stream of self-contained JSON objects, one per line (JSON Lines).
*   **Nested Objects**: Since fields like `message` are complex objects, the script stores them as serialized **JSON strings** in the `message` column to maintain data integrity and prevent Excel formatting errors.

## 🤝 Contributing
We welcome contributions! If you find a new field that needs parsing or improve the robustness of the JSON extraction logic, please feel free to open an issue or submit a pull request.

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```
