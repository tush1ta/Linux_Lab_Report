## Experiment: [Daily System Logger Script]
### Name:Tushita Sharma, Roll No.: 590029121 Date: 2025-10-24

### AIM:
* To create a shell script that logs current system information, rotates old logs, and schedules itself to run daily.

### Requirements:
* Any Linux Distro(kali)
* Any text editor (VS Code, Vim, Nano, etc.)  
* Cron service for scheduling  



### Theory:
In system administration, automated logging is crucial for monitoring system performance, diagnosing issues, and maintaining records.  
This experiment involves:
1. Logging details like username, date, processes, and disk usage.  
2. Archiving old logs automatically.  
3. Scheduling the script to run daily using `cron`.



### Procedure & Observations

#### **Exercise 1: Creating the Daily Log Script**

##### **Task Statement:**
Write a shell script that logs system info and handles automatic rotation of old logs.

##### **Explanation:**
This script:
- Identifies the current user.  
- Creates a directory for storing logs.  
- Saves daily logs with timestamps.  
- Archives logs older than 7 days.  
- Can be scheduled using a cron job.  

##### **Command(s):**

```bash
#!/bin/bash
SYS_D="$HOME/daily_logs"
ARCHIVE_DIR="$SYS_D/archive"
mkdir -p "$ARCHIVE_DIR"


LOG_FILE="$SYS_D/log_$(date +%Y-%m-%d).txt"


{
  echo "============================="
  echo "System Log for: $(date)"
  echo "User: $(whoami)"
  echo "============================="
  echo
  echo "Uptime:"
  uptime
  echo
  echo "Top 5 CPU-consuming processes:"
  ps -eo pid,comm,%mem,%cpu --sort=-%cpu | head -n 6
  echo
  echo "Disk Usage:"
  df -h
} > "$LOG_FILE"


find "$SYS_D" -name "log_*.txt" -mtime +7 -exec mv {} "$ARCHIVE_DIR" \;


if [ "$(date +%u)" -eq 7 ]; then
  tar -czf "$ARCHIVE_DIR/weeklylogs_$(date +%Y-%m-%d).tar.gz" -C "$ARCHIVE_DIR" .
fi
```
## Output Example:


<p align="center">
<img src="/.img/mid1.jpg" width="900">
</p>


## Exercise 2: Scheduling the Script
## Task Statement:
Schedule the above script to run daily using cron.

## Explanation:
Use crontab to automate the script execution at a fixed time every day.

## Command(s):
bash
crontab -l
Use date +%Y-%m-%d for file naming.

Use find . -name "log_*.txt" -mtime +7 to identify old files.

Check system storage with df -h.

For archiving, use tar -czf weeklylogs_$(date +%Y-%m-%d).tar.gz.

Store archives in ~/daily_logs/archive.

## Scheduling(cron job)
Using crontab -e to schedule the script to run everyday at a fixed time.
eg.
```
0 20 * * * /home/tushita/mid/mid.sh
```
<p align="center">
<img src="/.img/mid2.jpg" width="900">
</p>


## Result:
The script successfully logs daily system information, archives logs older than 7 days, and schedules itself to run daily using a cron job.



# 1.
### Enhancements and Exploration**

#### **Task Statement:**
Explore additional functionalities that can be added to the Daily System Logger script to improve automation, usability, and robustness.

#### Send an Email with Log Attachment**
You can send the latest log file via email using the `mail` command.  
This feature is useful for system administrators who want daily reports in their inbox.

##### **Example Implementation:**
```bash
# Send the latest log file as an email attachment
LOG_FILE="$LOG_DIR/log_$(date +%Y-%m-%d).txt"
mail -s "Daily System Log - $(date)" -a "$LOG_FILE" admin@example.com < /dev/null




```
# 2.

## Check if directories exist
```
if [ ! -d "$LOG_DIR" ]; then
    echo "Error: Log directory not found! Creating it now..."
    mkdir -p "$LOG_DIR"
fi
```
```
if [ ! -d "$ARCHIVE_DIR" ]; then
    echo "Error: Archive directory not found! Creating it now..."
    mkdir -p "$ARCHIVE_DIR"
fi
```
# Verify log file creation
```
if [ ! -f "$LOG_FILE" ]; then
    echo "Error: Failed to create log file." >&2
    exit 1
fi
```
## 3.
```bash
#!/bin/bash
echo "===== Daily Log Menu ====="
echo "1. View latest log"
echo "2. Archive old logs"
echo "3. Clean up old logs"
echo "4. Exit"
echo "=========================="
read -p "Enter your choice [1-4]: " choice

case $choice in
  1)
    echo "Showing latest log:"
    read $LOG_DIR
    cat "$LOG_DIR/log_$(date +%Y-%m-%d).txt"
    ;;
  2)
    echo "Archiving old logs..."
    tar -czf "$ARCHIVE_DIR/manual_archive_$(date +%Y-%m-%d).tar.gz" "$LOG_DIR"/log_*.txt
    echo "Archive created successfully."
    ;;
  3)
    echo "Deleting logs older than 7 days..."
    find "$LOG_DIR" -name "log_*.txt" -mtime +7 -exec rm {} \;
    echo "Old logs removed."
    ;;
  4)
    echo "Exiting..."
    exit 0
    ;;
  *)
    echo "Invalid option. Please try again."
    ;;
esac
```
## output:
<p align="center">
<img src="/.img/mid3.jpg" width="900">
</p>

<p align="center">
<img src="/.img/mid4.jpg" width="900">
</p>




## Conclusion:
The Daily System Logger script automates log creation, archiving, weekly compression, and local email delivery. It successfully runs daily using cron, demonstrating practical use of shell scripting for system monitoring.

We can simply check the mail by typing mail and typing 1 if its the latest mail on our system., also all of these mails only exist on my system and not on the internet, So even though its sent via email it doesn’t go to gmail or the internet it stays on my system