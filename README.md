# Personal Finance Tracker
A command-line Python application that allows users to log, categorize, and visualize their personal finances over time. The project features CSV-based data persistence, date-range filtering, and a Matplotlib graph to visualize income vs expenses.

---

## About the Project

By building a class-based CSV handler, I avoided the need for an external database — all data is stored and managed locally in a structured CSV file using Pandas. The application follows an interactive menu loop, where the user can add transactions or query their financial history by date range.

On the data side, I implemented date parsing and validation using Python's `datetime` module, and used Pandas DataFrame filtering with boolean masks to extract transactions within a given period. The visualization resamples the data by day and plots two separate time series — income and expenses — on the same chart.

---

## Tech Stack

**Language & Libraries:**

Python 3,

Pandas for data manipulation and CSV handling,

Matplotlib for time-series visualization,

CSV module for writing structured entries,

DateTime for date parsing and validation.

---

## Features & Design Decisions

**Data Persistence** — Transactions are stored in a local `finance_data.csv` file that is auto-created on first run if it doesn't exist.

**Transaction Logging** — Each entry captures date, amount, category (Income/Expense), and a description.

**Date Range Filtering** — Users can query all transactions between two dates using Pandas boolean masking.

**Financial Summary** — Automatically calculates and displays total income, total expenses, and net savings for the selected period.

**Visual Graph** — Plots daily income and expenses as a line chart using Matplotlib, resampled by day.

**Input Validation** — All user inputs (date, amount, category, description) are validated through a dedicated `data_entry.py` module.

---
## Project Files Explanation

**main.py** — Contains the `CSV` class which handles all file operations, the `plot_transactions` function for the graph, the `add()` function that collects user input, and the `main()` menu loop.

**data_entry.py** — Contains all input validation helpers: `get_date`, `get_amount`, `get_category`, and `get_description`. These ensure the user always provides correctly formatted data before it gets written to the CSV.

**finance_data.csv** — Auto-generated data file. Excluded from version control as it contains transaction data.

**.gitignore** — Excludes `finance_data.csv`, `.venv/`, `__pycache__/`, and `.idea/` from GitHub.

---

## Challenges & Progress

For the environment setup, I configured a virtual environment in PyCharm and installed Pandas and Matplotlib using the built-in package manager.

The main challenge was handling the time-series graph correctly — `reindex` was causing crashes due to duplicate dates and type mismatches between string columns and numeric fill values. I resolved this by selecting only the `amount` column before resampling, and using `.fillna(0)` instead of `reindex` to fill missing days.

I also identified a date format mismatch between the `FORMAT` constant and the user-facing prompts, which would have caused runtime crashes on date parsing — this was corrected to ensure consistency throughout the application.

---

## Getting Started

### Prerequisites
- Python 3.14
- pip
## Future Improvements

- [ ] Add a graphical user interface using Tkinter
- [ ] Export financial summaries to PDF
- [ ] Support for multiple currencies
- [ ] Monthly budget goals and spending alerts
- [ ] Migrate from CSV to SQLite for more robust data handling

---

## License

This project is open source and available under the [MIT License](LICENSE).
