# SysTrack Enterprise Automation & Remediation Scripts

PowerShell automation for SysTrack/Lakeside Software. 168 scripts, full module framework, complete documentation. Deploy and automate in under 10 minutes.

[![PowerShell](https://img.shields.io/badge/PowerShell-7.0+-5391FE?style=flat-square&logo=powershell&logoColor=white)](https://docs.microsoft.com/powershell/)
[![SysTrack](https://img.shields.io/badge/SysTrack-10.0+-00A4EF?style=flat-square)](https://www.lakesidesoftware.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![Scripts](https://img.shields.io/badge/Scripts-168-blue?style=flat-square)](#available-scripts)
[![Stars](https://img.shields.io/github/stars/wesellis/systrack-automation?style=flat-square)](https://github.com/wesellis/systrack-automation/stargazers)

---

## 🎯 What is SysTrack Automation?

Enterprise PowerShell automation framework for SysTrack/Lakeside Software operations. Automate remediation, monitoring, and endpoint management for digital experience monitoring (DEM) at scale.

### The Problem
IT teams spend hours manually fixing repetitive system issues detected by SysTrack. High CPU, memory leaks, network failures, application crashes - all require manual intervention.

### The Solution
- **168 PowerShell Scripts**: Automated remediation for common issues
- **PowerShell Module**: Import once, access all automation functions
- **Scheduled Automation**: Set-and-forget monitoring and remediation
- **SysTrack Integration**: Direct API integration for real-time responses
- **Enterprise-Ready**: ServiceNow, Teams, email notifications included

---

---

## 🚀 Quick Start

**New to the project? Start here:** [📖 QUICK_START.md](QUICK_START.md) - Deploy automation in under 10 minutes!

### Fast Setup (TL;DR)

```powershell
# 1. Clone Repository
git clone https://github.com/wesellis/systrack-automation.git
cd TECH-SysTrack-Lakeside-Enterprise-Automation-Remediation-Scripts

# 2. Import Module
Import-Module .\SysTrackAutomation.psd1

# 3. Initialize Environment
Initialize-SysTrackAutomation -CreateSampleConfig

# 4. Connect to SysTrack
Connect-SysTrack -Server "https://systrack.company.com"

# 5. Run Automation
Fix-HighCPUUsage -Threshold 90
Fix-MemoryLeaks
Fix-NetworkAdapters
```

**Need help?** See [QUICK_START.md](QUICK_START.md) for detailed setup, troubleshooting, and examples.

---

## Overview

Production-ready PowerShell automation framework for SysTrack/Lakeside Software. Comprehensive remediation scripts, monitoring automation, and endpoint management for enterprise IT operations.

## Features

- **Automated Remediation** - Scripts to fix common system issues
- **Performance Monitoring** - Extract and analyze metrics from SysTrack
- **Endpoint Management** - Bulk operations on devices
- **Report Generation** - Custom reports from SysTrack data
- **Alert Integration** - Connect to ticketing systems
- **Health Checks** - Proactive system maintenance

## Key Scripts

### Remediation Scripts

```powershell
# Auto-fix high CPU usage
.\Remediate-HighCPU.ps1 -Threshold 90 -Action "RestartService"

# Clear disk space automatically
.\Clear-DiskSpace.ps1 -MinFreeGB 10 -DeleteTempFiles -ClearLogs

# Fix network connectivity
.\Repair-NetworkConnection.ps1 -ResetAdapter -FlushDNS
```

### Data Collection

```powershell
# Get performance metrics
Get-SysTrackMetrics -Computer $computerName -Days 7 |
    Export-Csv "performance.csv"

# Extract user experience scores
Get-UserExperienceScore -Department "Finance" |
    Where {$_.Score -lt 70}

# Collect system inventory
Get-SysTrackInventory | Export-Excel "inventory.xlsx"
```

### Automated Actions

```powershell
# Restart services based on SysTrack alerts
Watch-SysTrackAlerts -Type "ServiceDown" -Action {
    Restart-Service $_.ServiceName -Force
}

# Update software when outdated
Get-OutdatedSoftware | Update-SoftwarePackage -Silent

# Reboot systems with issues
Get-SystemsNeedingReboot | Restart-Computer -Wait
```

## Quick Start

```powershell
# Import SysTrack module
Import-Module .\SysTrackAutomation.psd1

# Connect to SysTrack
Connect-SysTrack -Server "systrack.company.com" -Credential (Get-Credential)

# Run first remediation
Start-AutoRemediation -Scope "AllSystems"
```

## Script Categories

### Performance
- `Fix-HighMemory.ps1` - Memory leak remediation
- `Optimize-CPU.ps1` - CPU optimization
- `Clear-Cache.ps1` - Clear various caches
- `Defrag-Drives.ps1` - Disk defragmentation
- `Optimize-Services.ps1` - Service optimization

### Network
- `Test-Connectivity.ps1` - Network diagnostics
- `Reset-NetworkStack.ps1` - TCP/IP reset
- `Update-DNSServers.ps1` - DNS configuration
- `Fix-ProxySettings.ps1` - Proxy repairs
- `Optimize-Bandwidth.ps1` - Bandwidth management

### Applications
- `Repair-Office365.ps1` - Office repairs
- `Fix-Outlook.ps1` - Outlook issues
- `Clear-TeamsCache.ps1` - Teams optimization
- `Repair-Chrome.ps1` - Browser fixes
- `Reset-Applications.ps1` - App resets

### System Health
- `Run-HealthCheck.ps1` - System health audit
- `Update-Drivers.ps1` - Driver updates
- `Clean-Registry.ps1` - Registry cleanup
- `Fix-WindowsUpdate.ps1` - Update repairs
- `Optimize-Startup.ps1` - Boot optimization

### Reporting
- `Generate-DashboardData.ps1` - Dashboard metrics
- `Export-UserExperience.ps1` - UX reports
- `Get-TrendAnalysis.ps1` - Trend reports
- `Create-ExecutiveReport.ps1` - Executive summaries
- `Export-Compliance.ps1` - Compliance reports

## Configuration

### Settings File

```json
{
  "SysTrackServer": "systrack.company.com",
  "Database": "SysTrack_DB",
  "RemediationEnabled": true,
  "ThresholdCPU": 85,
  "ThresholdMemory": 90,
  "ThresholdDisk": 10,
  "AutoRebootAllowed": false,
  "NotificationEmail": "it-alerts@company.com"
}
```

### Alert-Based Automation

```powershell
# Configure auto-remediation rules
New-RemediationRule -Trigger "DiskSpace < 5%" `
                   -Action "Clear-TempFiles" `
                   -Notify "it-team@company.com"
```

### Scheduled Tasks

```powershell
# Schedule daily health checks
Schedule-SysTrackTask -Script "HealthCheck.ps1" `
                     -Time "06:00" `
                     -Recurrence Daily
```

### Integration Examples

```powershell
# ServiceNow integration
Send-ToServiceNow -Alert $sysTrackAlert `
                 -Priority "High" `
                 -AssignmentGroup "Desktop Support"

# Email notifications
Send-RemediationReport -Recipients "managers@company.com" `
                      -IncludeMetrics
```

### Custom Remediation

```powershell
# Define custom remediation
function Invoke-CustomFix {
    param($Computer, $Issue)

    switch ($Issue.Type) {
        "AppCrash" { Repair-Application $Issue.AppName }
        "SlowLogin" { Optimize-UserProfile $Issue.UserName }
        "NetworkDrop" { Reset-NetworkAdapter }
    }
}
```

## Monitoring Dashboard

Scripts include dashboard generators:

```powershell
# Generate HTML dashboard
New-SysTrackDashboard -OutputPath "C:\Dashboards" `
                     -RefreshInterval 300 `
                     -Metrics @("CPU","Memory","Disk","Network")
```

## Security

- **Credential Management** - Secure storage
- **Audit Logging** - All actions logged
- **RBAC** - Role-based permissions
- **Encrypted Connections** - Secure communications
- **Change Control** - Approval workflows

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Connection failed | Check SysTrack server accessibility |
| No data returned | Verify database permissions |
| Script timeout | Increase timeout values |
| Remediation failed | Check error logs in Event Viewer |

## Documentation

- [SysTrack API Reference](docs/api-reference.md)
- [Remediation Guide](docs/remediation-guide.md)
- [Best Practices](docs/best-practices.md)
- [Troubleshooting](docs/troubleshooting.md)

## Requirements

- PowerShell 7.0 or higher
- SysTrack 10.0 or higher
- Appropriate permissions for remediation actions
- Network access to SysTrack server

## Contributing

Contributions are welcome. Please follow PowerShell best practices and include appropriate documentation for new scripts.

## License

MIT License - See LICENSE file for details.

---

**Note**: These scripts are provided as-is for IT automation purposes. Test thoroughly in a non-production environment before deploying to production systems. Always follow your organization's change management procedures.

---
