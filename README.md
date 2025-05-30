
# Firewall Configuration Intern Task

![Windows](https://img.shields.io/badge/OS-Windows-0078D6?logo=windows)
![Linux](https://img.shields.io/badge/OS-Linux-FCC624?logo=linux)
![Firewall](https://img.shields.io/badge/Focus-Firewall_Configuration-red)

A complete implementation of Windows and Linux firewall configuration tasks, demonstrating rule creation, testing, and traffic filtering principles.


## 🛠️ Tasks Completed

### Windows Firewall
1. Opened firewall configuration tool (`wf.msc`)
2. Listed current rules (`netsh advfirewall show rule name=all`)
3. Blocked inbound Telnet (Port 23)
4. Verified rule effectiveness
5. *(Optional)* Allowed SSH (Port 22)
6. Restored original state

### Linux UFW
1. Accessed UFW via terminal
2. Listed current rules (`sudo ufw status numbered`)
3. Blocked Telnet (Port 23)
4. Allowed SSH (Port 22)
5. Tested configuration
6. Removed test rules

## 📚 Key Documentation

- [Windows Step-by-Step Guide](Windows/7_steps_used.md)
- [Linux Command Reference](Linux/5_commands_used.md)
- [Firewall Filtering Explained](8_firewall_filtering.md)

## 🧪 Testing Methodology

| Test Case               | Verification Method                     |
|-------------------------|-----------------------------------------|
| Port Blocking           | `Test-NetConnection` (Win) / `nc` (Linux) |
| Rule Persistence        | Reboot verification                     |
| Default Deny Policy     | Unauthorized port scan                  |
| Stateful Filtering      | TCP handshake analysis                  |

## 💻 Quick Start (Linux Example)

```bash
# Block Telnet
sudo ufw deny 23/tcp

# Allow SSH
sudo ufw allow 22/tcp

# Verify
sudo ufw status numbered
```

## 🔍 Technical Highlights

- **Port-based filtering** (TCP/UDP)
- **Application control** (Windows only)
- **Stateful inspection**
- **Rule precedence management**
- **Connection tracking**

## 📝 Notes

1. Windows screenshots show GUI + CLI methods
2. Linux implementation uses UFW (Uncomplicated Firewall)
3. All test rules are removed in final steps

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

<div align="center">
  <sub>Created with ❤️ for cybersecurity internship</sub>
</div>
```

