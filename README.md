# 📊 LogStream Parser: JSONL to Excel Utility

A powerful command-line tool for parsing Claude Code **JSON Lines (JSONL)** log files and exporting their data into structured Microsoft Excel (`.xlsx`) spreadsheets. This utility is designed for data analysts who need to efficiently extract specific, critical fields from massive amounts of unstructured system logs.

---

### ✨ Key Features
*   **Targeted Extraction:** Pulls precise, required fields (e.g., `timestamp`, `userType`, `parentUuid`) regardless of the JSONL's complexity or depth.
*   **Robust Handling:** Gracefully handles missing keys and malformed logs without crashing the entire process.
*   **Nested Data Support:** Safely extracts content from deeply nested structures (like message roles/content) and serializes them for Excel compatibility.
*   **CLI Integration:** Built for command-line use, making it perfect for automation pipelines.

### ⚙️ Installation
The tool requires Python 3.8+ and two libraries: `pandas` and `openpyxl`.

```bash
pip install pandas openpyxl
🚀 Usage Guide
Run the script by providing the source JSONL file path and the desired output directory.

📦 Basic Syntax
python jsonl_to_excel.py <SOURCE_JSONL_PATH> <OUTPUT_DIRECTORY> [--output-name FILENAME]
💡 Examples
1. Standard Export: Parses session.jsonl and saves the result in a new folder called analysis_reports.

python jsonl_to_excel.py ./data/session.jsonl ./analysis_reports
2. Custom Filename: Saves the log data but names the resulting file specifically for today's report.

python jsonl_to_excel.py ./logs/batch.jsonl ./results --output-name Daily_Report_YYYYMMDD.xlsx
🔍 Technical Details
Input Format: Must be JSON Lines (one complete, valid JSON object per line).
Output: Saves the structured data as an .xlsx file in the specified output directory.
Field Mapping: The script extracts and flattens key fields including parentUuid, type, timestamp, userType, and nested message details (message.role, message.content).
