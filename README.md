# 🛡️ blockips: An IP Blocking CLI Tool

![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)
![Platform](https://img.shields.io/badge/platform-Linux-green.svg)

A powerful, cumulative IP blocking tool for Linux systems that provides **dual-layer protection** using both iptables (system-level) and Apache .htaccess (web server-level) blocking.

## Features

### **Core Functionality**
- **Cumulative IP Blocking** - Add new IPs without removing existing blocks
- **Dual-Layer Protection** - System-level (iptables) + Web server-level (Apache) blocking
- **Persistent Storage** - Blocked IPs survive system reboots
- **Duplicate Prevention** - Won't block the same IP twice
- **Input Validation** - Validates IP address format before processing

### **Management Features**
- **List Blocked IPs** - View all currently blocked addresses
- **Unblock Individual IPs** - Remove specific IP addresses from block list
- **Clear All Blocks** - Remove all blocked IPs with confirmation prompt
- **Colored Output** - Easy-to-read status messages with color coding
- **Detailed Summaries** - See exactly what happened after each operation

### **Security Features**
- **Root Privilege Check** - Ensures proper permissions for system modifications
- **Custom iptables Chain** - Uses dedicated chain for organized rule management
- **Automatic Environment Setup** - Creates necessary directories and files
- **Safe Unblocking** - Removes rules from all blocking layers

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/blockips.git
cd blockips

# Make the script executable and install it
sudo cp blockips /usr/local/bin/
sudo chmod +x /usr/local/bin/blockips
```

## Usage Examples

```bash
# Block a single IP address
sudo blockips 192.168.1.100

# Block multiple IP addresses at once
sudo blockips 192.168.1.100 10.0.0.5 172.16.0.10

# List all currently blocked IPs
sudo blockips --list

# Unblock a specific IP address
sudo blockips --unblock 192.168.1.100

# Clear all blocked IPs (with confirmation)
sudo blockips --clear

# Show help and usage information
blockips --help

# Test with invalid IP (will be rejected)
sudo blockips 999.999.999.999 192.168.1.50

# Example output:
# ✗ Invalid IP address format: 999.999.999.999
# ✓ Blocked 192.168.1.50 in iptables
# 
# === SUMMARY ===
# New IPs blocked: 1
# Duplicate IPs (already blocked): 0
# Invalid IPs: 1
```

## 📋 Command Reference

| Command | Description | Example |
|---------|-------------|---------|
| `blockips <ip1> [ip2] ...` | Block one or more IP addresses | `sudo blockips 1.1.1.1 2.2.2.2` |
| `blockips --list` or `-l` | Show all currently blocked IPs | `sudo blockips --list` |
| `blockips --unblock <ip>` | Unblock a specific IP address | `sudo blockips --unblock 1.1.1.1` |
| `blockips --clear` | Remove all IP blocks (with confirmation) | `sudo blockips --clear` |
| `blockips --help` or `-h` | Show help and usage information | `blockips --help` |

### File Locations

- **Script Location**: `/usr/local/bin/blockips`
- **Blocked IPs Database**: `/var/lib/blockips/blocked_ips.txt`
- **Apache Rules**: `/var/www/html/.htaccess` (if Apache is installed)
- **iptables Chain**: `BLOCKIPS_INPUT`

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE](LICENSE) file for details.

## Future Enhancements

- [ ] Support for CIDR notation (e.g., 192.168.1.0/24)
- [ ] Integration with fail2ban
- [ ] Whitelist functionality
- [ ] Automatic unblocking after specified time
- [ ] IPv6 support
- [ ] Configuration file support
- [ ] Logging integration
- [ ] Web interface for management

---

**⭐ If you find this tool useful, please give it a star on GitHub!**
