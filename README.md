

#  SentinelScan – Advanced Process Threat Detector

**Author:** Derek Lenz

SentinelScan is a lightweight Python-based threat detection tool that scans running system processes, identifies potentially suspicious activity, and generates both terminal output and a professional PDF report.

---

##  Features

*  Scans all active system processes
   Detects potentially suspicious processes based on:

  * Non-system user execution
  * Unsigned binaries
  * Unknown process behavior
*  Displays results directly in the terminal
*  Generates a structured PDF report
*  Logs scan summaries for historical tracking
*  Simple heuristic-based detection logic (extendable)

---

##  How It Works

SentinelScan uses the `psutil` library to enumerate running processes and applies basic threat detection logic:

* Whitelisted system processes are ignored
* Processes not running under **NT AUTHORITY** are flagged
* Processes with suspicious naming (e.g., "Unsigned") are flagged
* Access errors are treated as suspicious (defensive approach)

---

##  Requirements

Install dependencies before running:

```bash
pip install psutil fpdf
```

---

##  Usage

Run the script:

```bash
python sentinel_scan.py
```

---

##  Example Output

```
=== SentinelScan: Advanced Process Threat Detector ===

Total processes scanned: 145
Suspicious processes detected: 7

Top 10 Suspicious Processes:
PID | Process Name | Username | Parent Name | Flags_Display
----------------------------------------------------------
1234 | suspicious.exe | user-PC | explorer.exe | Unknown hash, Unsigned binary
```

---

##  Output Files

After execution, the tool generates:

*  **PDF Report**

  ```
  process_scan_report_YYYYMMDD_HHMMSS.pdf
  ```

  Includes:

  * Scan summary
  * Top suspicious processes
  * Structured table output

*  **Log File**

  ```
  sentinel_scan.log
  ```

  Tracks scan history with timestamps

---

##  Detection Logic (Current Version)

```python
return not proc.username().startswith("NT AUTHORITY") or "Unsigned" in name
```

This is a **basic heuristic model** and can be expanded with:

* Hash checking (VirusTotal / OTX)
* Behavioral analysis
* Parent-child process anomaly detection
* Network activity correlation

---


##  Disclaimer

This tool is intended for **educational and defensive cybersecurity purposes only**.
It is not a replacement for enterprise-grade security tools.

---

##  Portfolio Value

This project demonstrates:

* Python scripting for cybersecurity
* Process analysis using `psutil`
* Threat detection logic
* Report generation (FPDF)
* Logging and automation

 Perfect for roles in:

* SOC Analyst
* Threat Hunter
* Cybersecurity Analyst

---

##  Project Structure

```
sentinel_scan.py
sentinel_scan.log
process_scan_report_*.pdf
```





