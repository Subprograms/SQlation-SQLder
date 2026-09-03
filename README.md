# SQLation / SQLder

Build and practice on SQL queries with SQLder, then fire up a simulated SQL database to query from via SQLation.py

---

## Overview

This suite provides a hands-on learning environment featuring two main components:

1. **SQL Practice Worksheet**: A practical exercise file designed to build, refine, and practice essential relational database querying concepts.
2. **Python SQL Query Simulator**: An interactive, terminal-based database engine that automatically loads setup files, executes read-only SQL queries in an in-memory SQLite database, and logs outputs directly to CSV files.

---

## Features

* **Zero External Dependencies**: Built entirely with standard Python standard libraries (`sqlite3`, `tkinter`, `csv`, `os`, `re`).
* **GUI File Selection**: Native OS file pickers for selecting setup files and target CSV output directories.
* **In-Memory Execution**: Loads schema and datasets into an isolated SQLite in-memory database for fast, side-effect-free execution.
* **Automated Data Processing**:
* Parses setup scripts while automatically stripping SQL comments (`--`, `/* */`).
* Auto-renames target tables to follow `<setup_filename>_db`.
* Generates a full database CSV snapshot upon startup.
* Automatically logs every executed query result to a daily export file formatted as `<setup_filename>_db_query_MM-DD-YYYY.csv`.


* **Formatted Terminal Output**: Aligns query results dynamically into clean ASCII tables with row count indicators.

---

## Repository Structure

Simply download and extract the repository `.zip` archive. The directory is structured as follows:

* **SQL_Practice_Worksheet.txt**: Hands-on SQL practice exercises, setup statements, and target queries.
* **main.py**: Interactive Python SQL Simulator script.
* **README.md**: Project documentation.

---

## Quick Start & Setup

**Prerequisites**

* **Python 3.x** installed on your system.
* No additional `pip install` commands are required.

**Installation**

1. Download the repository `.zip` file from GitHub.
2. Extract the contents of the `.zip` file into any directory on your computer.
3. Open a terminal or command prompt in the extracted directory.

---

## Usage Guide

**1. Running the Simulator**

Start the application by running the main Python script:

`python main.py`

When launched, the program will open native GUI file dialogs:

1. **SQL Setup File Picker**: Select your SQL setup file (e.g., `SQL_Practice_Worksheet.txt`).
2. **Database CSV Directory**: Select a destination directory to store the full database export (`<setup_filename>_db.csv`).
3. **Query Export Directory**: Select a directory where your daily query outputs will be saved.

**2. Interactive Querying**

Once the database finishes initialization, you will be brought to the `SQL>` terminal prompt.

* **Single Query per Line**: Input one query per line and press **ENTER** to execute immediately.
* **Exit Program**: Type **EXIT** or **exit** at the prompt to end the session.

---

## SQL Syntax & Capabilities

The engine supports standard ANSI SQL syntax via SQLite:

* **Core Clauses**: `SELECT`, `FROM`, `WHERE`, `GROUP BY`, `HAVING`, `ORDER BY (ASC / DESC)`
* **Common Table Expressions**: `WITH` clauses for modular query building.
* **Aggregations**: `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`
* **String Transformations**: `UPPER()`, `LOWER()`, `LENGTH()`, `SUBSTR()`
* **Logical Operations**: `LIKE`, `IN`, `BETWEEN`, `CASE WHEN ... THEN ... ELSE END`

*Note: To prevent accidental state modification, interactive execution is restricted to read-only queries (`SELECT`, `WITH`). Table creation and data insertion are handled automatically during the initial setup step.*

---

## File & Table Naming Conventions

The program automatically normalizes filenames and table identifiers based on your setup file name:

| Component | Format | Example (Setup file: `practice_data.txt`) |
| --- | --- | --- |
| **Database Table** | `<setup_filename>_db` | `practice_data_db` |
| **Full Database CSV** | `<setup_filename>_db.csv` | `practice_data_db.csv` |
| **Daily Query Export** | `<setup_filename>_db_query_MM-DD-YYYY.csv` | `practice_data_db_query_09-03-2026.csv` |

---

## Worksheet Integration

The included `SQL_Practice_Worksheet.txt` works directly with the simulator:

1. Review the practice questions and schema layout outlined inside the worksheet.
2. Select `SQL_Practice_Worksheet.txt` when prompted by `main.py` at startup.
3. Formulate your SQL queries to solve each exercise, entering them directly into the terminal prompt.
4. Verify your results using the formatted terminal output tables or check the exported query CSV files.

---

## Troubleshooting

* **GUI Window Not Showing**: Check your system taskbar; native pop-ups may occasionally open behind active terminal windows.
* **"Only SELECT and WITH queries are allowed"**: Modifying statements (`INSERT`, `UPDATE`, `DROP`) must be included directly inside your setup `.txt` file prior to launching query mode.
