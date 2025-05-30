
# Windows Firewall Configuration - Step-by-Step Guide

## Open Firewall Configuration Tool

### GUI Method:
1. Press `Windows Key + R` to open Run dialog  
2. Type `wf.msc` and press Enter  
3. Verify you see:  
   - "Windows Defender Firewall with Advanced Security" window  
   - Three sections: Inbound Rules, Outbound Rules, Monitoring  

---

### CLI Method:

```cmd
:: Open classic firewall interface
control firewall.cpl

:: Check current profile status
netsh advfirewall show currentprofile
````

---

### List Current Firewall Rules

**Key Filters:**

```powershell
# View only active inbound rules
Get-NetFirewallRule -Direction Inbound -Enabled True | Format-Table -AutoSize

# View rules blocking ports
Get-NetFirewallPortFilter | Where-Object { $_.Action -eq "Block" }
```

---

### Block Inbound Telnet (Port 23)

**Rule Creation:**

```cmd
:: Create block rule
netsh advfirewall firewall add rule name="Block Telnet Port 23" dir=in action=block protocol=TCP localport=23

:: Verify rule
netsh advfirewall firewall show rule name="Block Telnet Port 23"
```

**Screenshot done:**
Captured "New Inbound Rule Wizard" showing:

* Port selection (TCP 23)
* Block action selected

---

### Test the Block Rule

**Pre-Block Test:**

```powershell
# Check if port is initially open
Test-NetConnection -ComputerName localhost -Port 23 | Select-Object TcpTestSucceeded
```

**Post-Block Test:**
*Expected result: False*

```powershell
Test-NetConnection -ComputerName localhost -Port 23 |
    Select-Object @{n="TestTime";e={Get-Date}}, TcpTestSucceeded, SourceAddress, RemotePort
```

---

### Restore Original State

**Rule Removal:**

```cmd
:: Delete the test rule
netsh advfirewall firewall delete rule name="Block Telnet Port 23"

:: Verification
netsh advfirewall firewall show rule name="Block Telnet Port 23" || echo "Rule successfully removed"
```


