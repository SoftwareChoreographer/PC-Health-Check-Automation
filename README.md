
# 🖥️ PC Health Monitor + Alert System

**Automated monitoring of CPU, RAM, disk, and network performance with real-time alerts.**  
A practical IT support project that demonstrates proactive troubleshooting and enterprise-ready monitoring skills.

## 🎯 Project Overview

This tool continuously tracks key system health metrics and provides alerts when usage crosses safe thresholds.  
It helps IT professionals prevent downtime, troubleshoot performance issues, and automate reporting.

| Metric | What It Tracks | Default Threshold |
|--------|---------------|-------------------|
| CPU    | Processor load | > 85% usage |
| RAM    | Memory usage   | > 80% usage |
| Disk   | Free space     | < 15% available |
| Network| (Optional) Upload/Download speed | TBD |

---

## 🚀 Quick Start

### Prerequisites
```powershell
# Requires Windows PowerShell 5.1+
# Some features may need Administrator privileges
```

### Example Run
```powershell
# Basic health check (one-time)
.\PCHealthMonitor.ps1

# Continuous monitoring every 60 seconds with logging
.\PCHealthMonitor.ps1 -Interval 60 -LogPath "C:\Logs\Health.log"

# With email alerts for IT admin
.\PCHealthMonitor.ps1 -Interval 60 -Email "admin@company.com"
```

**Parameters:**
- `-Interval` → Number of seconds between checks (default: 0 = run once)
- `-LogPath` → Path to save log file (CSV format)
- `-Email` → Send alerts to this address (via SMTP)
- `-CpuThreshold`, `-RamThreshold`, `-DiskThreshold` → Custom limits

---

## 📋 Features

- ✅ **CPU Monitoring** – Detects high processor usage
- ✅ **Memory Tracking** – Alerts on excessive RAM consumption
- ✅ **Disk Monitoring** – Warns when free space is critically low
- ✅ **Logging** – Saves results to logs/CSV for analysis
- ✅ **Email Alerts** – Sends notifications when thresholds are exceeded
- ✅ **Configurable** – Customize thresholds, intervals, and log locations

---

## 🏗️ Project Structure

```
pc-health-monitor/
│
├── 📄 README.md               # Documentation
├── 📄 LICENSE                 # MIT
├── 📁 scripts/
│   └── PCHealthMonitor.ps1    # Main script
├── 📁 sample_data/
│   └── sample_report.csv      # Example output
├── 📁 logs/
│   └── (generated logs)
```

---

## 📸 Example Output

```
[2025-09-09 22:15:00] CPU: 42% | RAM: 63% | Disk C:: 22% free
[2025-09-09 22:16:00] CPU: 88% ⚠️ ALERT: CPU usage exceeded 85%
[2025-09-09 22:17:00] RAM: 91% ⚠️ ALERT: RAM usage exceeded 80%
```

Sample alert email:
```
Subject: ⚠️ PC Health Alert - High CPU Usage
Body: CPU usage has reached 92% at 2025-09-09 22:16:00
```

---

## 💼 Business Value

- **Proactive Monitoring** → Detects problems before they impact users  
- **Time Savings** → Automated checks replace manual diagnostics  
- **Consistency** → Standardized reporting for every system  
- **Scalability** → Deploy across multiple endpoints with minimal setup  

---

## 🔧 Deployment

### Option 1: Manual Run
Technicians run the script as needed for diagnostics.

### Option 2: Scheduled Task (Recommended)
```powershell
# Schedule health checks every 5 minutes
$Action = New-ScheduledTaskAction -Execute "powershell.exe" -Argument "-File C:\Scripts\PCHealthMonitor.ps1 -Interval 0 -LogPath C:\Logs\Health.log"
$Trigger = New-ScheduledTaskTrigger -Once -At (Get-Date).Date -RepetitionInterval (New-TimeSpan -Minutes 5)
Register-ScheduledTask -Action $Action -Trigger $Trigger -TaskName "PC Health Monitor" -Description "Monitors CPU, RAM, and disk usage"
```

---

## 🛡️ Security & Safety

- ✅ **Read-only monitoring** – No destructive changes made  
- ✅ **Safe logging** – Stores system data without exposing sensitive info  
- ✅ **Controlled alerts** – Only sends configured notifications  

---

## 📚 Learning Resources

- [PowerShell Monitoring Cmdlets](https://learn.microsoft.com/en-us/powershell/)  
- [System.Diagnostics.PerformanceCounter](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.performancecounter)  
- [Windows Task Scheduler](https://docs.microsoft.com/en-us/windows/win32/taskschd/about-the-task-scheduler)  

---

## 📄 License

MIT License – Free to use, modify, and distribute. Attribution appreciated.

---

## 🏆 Portfolio Highlights

This project demonstrates:  
- ✅ **System monitoring expertise**  
- ✅ **Proactive IT support automation**  
- ✅ **Professional logging & reporting**  
- ✅ **Real-world deployment via Task Scheduler**  
- ✅ **Business impact awareness (proactive vs reactive support)**  

---

## 🌟 Future Enhancements

- [ ] Add **Slack/MS Teams integration** for alerts  
- [ ] Build a **web dashboard** (Flask + Chart.js)  
- [ ] Collect **network statistics** (latency, throughput)  
- [ ] Centralize logs from multiple PCs into one report  
