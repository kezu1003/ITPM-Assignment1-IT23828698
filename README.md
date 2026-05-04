# Singlish to Sinhala Transliteration - Test Automation
### Student ID: IT23828698

This project contains automated test cases for evaluating the accuracy of the **Chat Sinhala transliteration** function available at [PixelsSuite Chat Translator](https://www.pixelssuite.com/chat-translator).

The tests are built using **Playwright** and **Python**, and results are automatically recorded in an Excel file.

---

## Project Structure

```
IT23828698/
│
├── test_automation.py            # Main Playwright test script
├── IT23828698.xlsx               # Excel file with test cases and results
├── Commands.txt                  # Quick reference commands
└── README.md                     # Project documentation
```

---

## Prerequisites

Before running the tests, make sure the following are installed on your machine:

- **Python 3.11 or 3.12** — [Download here](https://www.python.org/downloads/)
- **Google Chrome** browser (recommended)

> ⚠️ When installing Python, make sure to check **"Add Python to PATH"** during installation.

---

## Installation

### Step 1 — Extract the project folder

Extract the ZIP file to your **D: drive**:

```
D:\IT23828698
```

### Step 2 — Open Command Prompt

Press `Windows + R`, type `cmd`, and press Enter.

Navigate to the project folder:

```cmd
cd /d D:\IT23828698
```

### Step 3 — Install dependencies

Run the following commands one by one:

```cmd
"C:\Program Files\Python312\python.exe" -m pip install -U pip
```

```cmd
"C:\Program Files\Python312\python.exe" -m pip install playwright openpyxl
```

```cmd
"C:\Program Files\Python312\python.exe" -m playwright install
```

> The last command downloads the required browsers (Chrome, Firefox, WebKit). This may take a few minutes.

---

## Running the Tests

### Step 1 — Prepare the Excel file

Make sure `IT23828698.xlsx` is in the project folder and:
- Columns A to D are filled (TC ID, Input length type, Input, Expected output)
- Columns E and F are **left blank** — the script fills these automatically

### Step 2 — Close the Excel file

Make sure `IT23828698.xlsx` is **completely closed** before running the script.

### Step 3 — Run the test script

From the Command Prompt (inside `D:\IT23828698`), run:

```cmd
"C:\Program Files\Python312\python.exe" test_automation.py --excel "IT23828698.xlsx" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 8000 --type-delay-ms 100 --slow-mo-ms 300 --save-every 1 --keep-open
```

### What happens during the run

- A browser window opens automatically
- The script navigates to the Chat Translator website
- Each Singlish input is typed into the input box
- The Sinhala output is captured and compared with the expected output
- Results (Actual output + Pass/Fail status) are saved to `IT23828698.xlsx` automatically

### Step 4 — Stop the script

Once all test cases are completed, press `Ctrl + C` in Command Prompt to close the browser.

### Step 5 — Check results

Open `IT23828698.xlsx` and verify:
- Column E — **Actual output** (captured from the website)
- Column F — **Status** (FAIL for all negative test cases)

---

## Command Parameters

| Parameter | Description | Value used |
|---|---|---|
| `--excel` | Path to the Excel test case file | IT23828698.xlsx |
| `--url` | URL of the application under test | https://www.pixelssuite.com/chat-translator |
| `--wait-ms` | Wait time (ms) after transliteration before capturing output | 8000 |
| `--type-delay-ms` | Delay (ms) between each character typed | 100 |
| `--slow-mo-ms` | Slow motion delay (ms) for browser actions | 300 |
| `--save-every` | Save results to Excel after every N test cases | 1 |
| `--keep-open` | Keep browser open after tests complete | Enabled |

---

## Test Case Overview

- **Total test cases:** 50
- **Type:** Negative test cases (all expected to FAIL)
- **TC ID format:** Neg_0001 to Neg_0050
- **Input types covered:** All 24 Singlish input types as specified in Appendix 1

### Input Length Categories

| Code | Description |
|---|---|
| S | Short — 30 characters or less |
| M | Medium — 31 to 299 characters |
| L | Long — 300 to 450 characters |

---

## Troubleshooting

**Permission denied error on Excel file**
- Make sure `IT23828698.xlsx` is fully closed before running the script

**Output did not update error**
- Increase the `--wait-ms` value (e.g. try `--wait-ms 12000`)

**Python not recognized**
- Use the full path: `"C:\Program Files\Python312\python.exe"` instead of just `python`

**Failed to fetch on the website**
- The transliteration API may be temporarily down
- Wait a few minutes and try again
- Try switching to mobile data or a different network

---

## Dependencies

| Package | Version | Purpose |
|---|---|---|
| playwright | 1.59.0 | Browser automation |
| openpyxl | 3.1.5 | Reading and writing Excel files |

---

## Notes

- Only the **Chat Sinhala** transliteration function is tested
- Standard Sinhala, backend APIs, performance, and security testing are out of scope
- All 50 test cases are negative — they are designed to expose failures in the transliteration system
- Submitted as part of IT3040 – ITPM Assignment 1, Semester 1
