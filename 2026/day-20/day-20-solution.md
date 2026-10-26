# Day 20 – Bash Scripting Challenge: Log Analyzer and Report Generator

## Objective

The objective of this project is to automate log file analysis using Bash scripting. The script identifies errors, extracts critical events, finds the most common error messages, and generates a daily summary report for easier monitoring and troubleshooting.

## 1. Log File Validation

**File:** `log_analyzer.sh`

### Features
- Accepts a log file path as a command-line argument.
- Displays an error message if no argument is provided.
- Validates whether the specified log file exists.
- Stops execution if the input is invalid.

### Usage

```bash
./log_analyzer.sh sample_log.log
```

### Sample Output

```text
Error: Usage: ./log_analyzer.sh <log_file>
```

*Note: This message appears when the script is executed without a log file argument.*

## 2. Error Count Analysis

### Features
- Counts lines containing `ERROR` or `Failed`.
- Displays the total error count.
- Uses `grep` to search for matching log entries.

### Sample Output

```text
===== Log Analysis Summary =====
Analysis Date: 2026-10-26
Log File: sample_log.log
Total Lines Processed: 15
Total Error Count: 10
```

*Note: The counts depend on the contents of the input log file.*

## 3. Critical Events Detection

### Features
- Searches for log entries containing `CRITICAL`.
- Displays critical events with their corresponding line numbers.
- Helps identify important system events for troubleshooting.

### Sample Output

```text
--- Critical Events ---
Line 6: 2026-10-26 09:25:00 CRITICAL Disk space below threshold
Line 10: 2026-10-26 09:45:00 CRITICAL Database connection lost
```

## 4. Top 5 Error Messages

### Features
- Extracts log entries containing `ERROR`.
- Identifies the most frequently occurring error messages.
- Sorts messages by occurrence count in descending order.
- Displays up to five common error messages.

### Sample Output

```text
--- Top 5 Error Messages ---
3 Connection timed out
3 File not found
1 Permission denied
1 Disk I/O error
```

*Note: The number of displayed messages depends on how many distinct error messages are present in the log file.*

## 5. Summary Report Generation

### Features
- Generates a report using the current date.
- Saves the analysis results in a text file.
- Includes the log file name and total lines processed.
- Records the total error count.
- Includes the top error messages and critical events.

### Report Filename

```text
log_report_2026-10-26.txt
```

### Sample Report Structure

```text
===== Log Analysis Report =====
Analysis Date: 2026-10-26
Log File: sample_log.log
Total Lines Processed: 15
Total Error Count: 10

--- Top 5 Error Messages ---
3 Connection timed out
3 File not found
1 Permission denied
1 Disk I/O error

--- Critical Events ---
Line 6: 2026-10-26 09:25:00 CRITICAL Disk space below threshold
Line 10: 2026-10-26 09:45:00 CRITICAL Database connection lost
```

*Note: The report contents depend on the actual log file and script execution date.*

## 6. Commands and Tools Used

| Command | Purpose |
|---|---|
| `grep` | Searches for errors and critical events |
| `sed` | Extracts error message text |
| `awk` | Processes log entries and line numbers |
| `sort` | Sorts error messages |
| `uniq` | Counts repeated messages |
| `head` | Displays the top five results |
| `wc` | Counts the total number of lines |
| `date` | Generates the report date |
| `Bash` | Automates the log analysis workflow |

## 7. How to Execute

Make the script executable:

```bash
chmod +x log_analyzer.sh
```

Run the script against the sample log file:

```bash
./log_analyzer.sh sample_log.log
```

View the generated report:

```bash
cat log_report_$(date +%Y-%m-%d).txt
```

## 8. What I Learned

1. **Bash Scripting:** Learned how to validate command-line arguments, handle files, and automate log analysis.
2. **Linux Text Processing:** Practiced using commands such as `grep`, `sed`, `awk`, `sort`, and `uniq` to extract and analyze log information.
3. **Report Automation:** Learned how to generate daily reports containing error statistics and critical events for system monitoring and troubleshooting.

## Conclusion

This project provided hands-on experience with Bash scripting, Linux text-processing commands, log analysis, and automated report generation. These skills are useful for troubleshooting system issues and automating routine DevOps and system administration tasks.

**Challenge:** 90 Days of DevOps  
**Day:** 20  
**Topics:** Bash Scripting | Log Analysis | Error Detection | Critical Events | Report Generation | Linux Automation
