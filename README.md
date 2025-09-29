# IP Blocking CLI Tool: blockips

## Features:
1. **System-level blocking:** Creates iptables rules in a custom chain BLOCKIPS_INPUT
2. **Apache Web server blocking:** Adds Deny from IP rules to /var/www/html/.htaccess
3. **Persistence:** Maintains a list in /var/lib/blockips/blocked_ips.txt
4. **Cumulative:** Each run adds new IPs without removing existing ones
5. **Persistent storage** - IPs are stored in /var/lib/blockips/blocked_ips.txt
6. **Input validation** - Validates IP address format
7. **Management commands** - List, unblock, and clear functionality

## Usage Examples:
```bash
# Block single or multiple IPs
sudo blockips 192.168.1.100 10.0.0.5 172.16.0.10

# List all currently blocked IPs
sudo blockips --list

# Unblock a specific IP
sudo blockips --unblock 192.168.1.100

# Clear all blocked IPs
sudo blockips --clear

# Show help
blockips --help
```
