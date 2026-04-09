# Web Server Log Analysis

## 📌 Overview
This project analyzes web server log data to extract meaningful insights such as traffic patterns, error trends, and bandwidth usage. The dataset consists of semi-structured log entries, which were processed and analyzed using Python and Pandas.

---

## 🎯 Objective
- Load and process compressed `.gz` log data
- Parse semi-structured log entries
- Perform data cleaning and preprocessing
- Analyze server activity using Pandas
- Extract actionable insights

---

## 🗂️ Dataset Description
Each log entry follows the format:

host - - [timestamp] "request" status bytes

Example:
199.72.81.55 - - [01/Jul/1995:00:00:01 -0400] "GET /index.html HTTP/1.0" 200 6245

### Extracted Fields:
- Host → Source of request  
- Timestamp → Date & time of request  
- Request → HTTP method + resource + protocol  
- Status → Response code  
- Bytes → Size of response  

---

## ⚙️ Approach

### 1. Data Loading
- Used `gzip` module to read compressed `.gz` file
- Loaded data line-by-line for memory efficiency

### 2. Data Parsing
- Used Regular Expressions (`re`) to extract structured fields:
  - host, timestamp, request, status, bytes

### 3. Data Cleaning
- Converted timestamps to datetime
- Replaced missing byte values (`-`) with `0`
- Converted data types:
  - status → int  
  - bytes → int  
- Removed invalid/malformed records

### 4. Feature Engineering
- Extracted:
  - date
  - hour
  - filename
  - file extension

### 5. Data Analysis
Performed analysis using Pandas:

- Total log records
- Unique hosts
- Date-wise unique filenames
- Count of 404 errors
- Top 404 filenames
- Top 404 file extensions
- Bandwidth usage per day (July 1995)
- Hourly request distribution
- Most requested files
- Status code distribution

---

## 📊 Key Insights
- Identified peak traffic hours using hourly distribution
- Observed frequent 404 errors for specific files
- Determined bandwidth usage trends across days
- Analyzed server response patterns using status codes

---

## 🚀 Technologies Used
- Python
- Pandas
- Regex (re)
- Datetime
- Gzip

---

## 📁 Project Structure
```
calgary-http-assessment/
│
├── analysis.ipynb
├── analysis.html
├── transcript.txt
├── README.md

```

---

## ⚠️ Assumptions
- Missing byte values (`-`) are treated as 0
- Invalid rows are skipped during parsing
- Only valid timestamps are considered for analysis

---

## 💡 Challenges Faced
- Handling semi-structured log data
- Designing regex for parsing
- Managing missing and inconsistent values
- Ensuring memory-efficient data loading

---

## ✅ Conclusion
This project demonstrates the ability to process raw log data, perform data cleaning, and extract meaningful insights using Python and Pandas. It highlights practical skills in data analysis, problem-solving, and real-world data handling.
