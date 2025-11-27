# Assignment 2: Linux & Shell Scripting Tasks
**Name:** Tushita Sharma
**Roll No.:** 590029121
**Date:** 2025-09-23

## Aim
To perform scripting and system tasks covering file renaming, searching, Fibonacci generation, permission checks, system info, monitoring, text statistics, sorting, GCD/LCM, palindrome checks, and string operations.

## Requirements
- Linux system with bash
- Terminal access
- Text editor (nano/vim)

---

## Task 1: Add Prefix or Suffix to All Files in a Directory
**Script**
```bash
#!/bin/bash
read -p "Enter prefix or suffix (prefix: p:TEXT or suffix: s:TEXT): " opt
for f in *; do
  if [[ -f "$f" ]]; then
    if [[ "$opt" == p:* ]]; then
      p=${opt#p:}
      mv "$f" "${p}${f}"
    elif [[ "$opt" == s:* ]]; then
      s=${opt#s:}
      mv "$f" "${f}${s}"
    fi
  fi
done
```
**Output**

![.](/.img/I1.png)
---

## Task 2: Recursive File Search (by extension or size)
**Commands**
```bash
# Find by extension (e.g., .log)
find ~ -type f -name "*.log"

# Find files larger than 1MB
find ~ -type f -size +1M
```
**Output**

![.](/.img/I2.png)
---

## Task 3: Fibonacci Series up to N terms
**Script**
```bash
#!/bin/bash
read -p "Enter limit: " n
a=0; b=1
for ((i=0;i<n;i++)); do
  echo -n "$a "
  fn=$((a+b))
  a=$b
  b=$fn
done
echo
```
**Example Output**
```
Enter limit: 8
0 1 1 2 3 5 8 13
```
output:
![.](/.img/I3.png)

---

## Task 4: Check File Readable/Writable/Executable
**Commands**
```bash
read -p "Enter filename: " f
[ -r "$f" ] && echo "Readable" || echo "Not readable"
[ -w "$f" ] && echo "Writable" || echo "Not writable"
[ -x "$f" ] && echo "Executable" || echo "Not executable"
```
**Output**

![.](/.img/I4.png)
---

## Task 5: Display System Information
**Commands**
```bash
date
uptime
who
free -h
df -h
```
**Output**
![.](/.img/I5.png)

---

## Task 6: Continuously Monitor and Log Top Memory-Consuming Processes
**Script (one-shot)**
```bash
top -b -o %MEM -n 1 | head -20
```
**Script (continuous logging every minute)**
```bash
#!/bin/bash
while true; do
  echo "--- $(date) ---" >> memlog.txt
  top -b -o %MEM -n 1 | head -20 >> memlog.txt
  sleep 60
done
```
**Output**
![.](/.img/I6.png)

---

## Task 7: Count Lines, Words, Characters of a File
**Commands**
```bash
wc -l cpu.sh
wc -w cpu.sh
wc -m cpu.sh
wc cpu.sh

```
**Output**

![.](/.img/I7.png)
---

## Task 8: Accept Multiple Numbers and Sort Ascending
**Commands**
```bash
read -p "Enter numbers separated by spaces: " nums
echo $nums | tr ' ' '
' | sort -n | tr '\n' ' '
echo
```
**Output**

![.](/.img/I8.png)
---

## Task 9: Calculate GCD and LCM of Two Numbers
**Script**
```bash
#!/bin/bash
read -p "Enter two numbers: " a b
gcd() {
  local x=$1 y=$2 r
  while [ $y -ne 0 ]; do
    r=$(( x % y ))
    x=$y
    y=$r
  done
  echo $x
}
g=$(gcd $a $b)
l=$(( (a / g) * b ))
echo "GCD = $g"
echo "LCM = $l"
```
**Output**

![.](/.img/I9.png)
---

## Task 10: Check Palindrome String
**Commands**
```bash
read -p "Enter string: " s
rev=$(echo "$s" | rev)
if [[ "$s" == "$rev" ]]; then
  echo "Palindrome"
else
  echo "Not palindrome"
fi
```
**Output**
![.](/.img/I10.png)
---

## Task 11: Length of a String
**Commands**
```bash
read -p "Enter string: " s
echo "Length: ${#s}"
```
**Output**

![.](/.img/I11png)
---

## Task 12: Reverse a Given String
**Commands**
```bash
read -p "Enter string: " s
echo "Reverse: $(echo "$s" | rev)"
```
**Output**

![.](/.img/I12.png)
---

## Task 13: Concatenate Two Input Strings
**Commands**
```bash
read -p "Enter first string: " s1
read -p "Enter second string: " s2
echo "Concatenated: ${s1}${s2}"
```
**Output**
![.](/.img/I13.png)

---

## Result
All tasks cover common scripting patterns, file operations, monitoring, and string/number processing useful for system administration and scripting practice.

## Conclusion
Assignment 2 provides practical tasks to strengthen shell scripting and Linux command-line proficiency.
