# V2Ray-X-UI
X-UI, a multi-user Xray graphical management panel (replacing V2-UI and V2Ray)



markdown
# X-UI Panel Setup Guide

A comprehensive guide to installing and configuring the X-UI panel for managing multiple proxy users.

## 🌟 Features
- Multi-protocol support (VMess, VLess, Trojan, Shadowsocks)
- TLS automatic certificate application/renewal
- Multi-user traffic statistics
- Customizable web interface
- System performance monitoring

## ⚙️ Installation
### Automatic Installation
```bash
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
Manual Installation
Download the latest binary:

bash
wget https://github.com/vaxilu/x-ui/releases/latest/download/x-ui-linux-amd64.tar.gz
Extract files:

bash
tar zxvf x-ui-linux-amd64.tar.gz
Move to system directory:

bash
cd x-ui
mv x-ui /usr/local/x-ui
🚀 Post-Installation
Access the panel at: http://your_server_ip:54321

Default credentials:

text
Username: admin
Password: admin
Important: Change default password immediately after login

🔧 Configuration
Adding Inbound Protocols
Navigate to Inbound List > Add Inbound

Configure settings:

Port: 443 (recommended)

Protocol: VMess/VLess/Trojan

Enable TLS (required for HTTPS)

SNI: Your domain name

Clients: Add users with unique UUIDs

Certificate Setup
bash
x-ui
> 16 (Certificate Management)
> 1 (Apply Certificate via Acme)
> Enter your domain name
📊 User Management
For each client:

Generate unique UUID (uuidgen command)

Set traffic limits (optional)

Specify email for identification

Client connection info includes:

Server IP/Domain

Port

UUID

Transport protocol (WS/TCP)

Path (for WebSocket)

TLS settings

🔄 System Commands
Command	Function
x-ui	Show control menu
x-ui start	Start service
x-ui stop	Stop service
x-ui enable	Enable auto-start
x-ui disable	Disable auto-start
x-ui status	Check service status
📎 Important Notes
Security Recommendations:

Always change default credentials

Use firewall (UFW) to restrict access:

bash
ufw allow 443/tcp
ufw allow 54321/tcp
ufw enable
Regularly update the panel:

bash
x-ui
> 11 (Update)
Troubleshooting:

Check logs: /etc/x-ui/x-ui.log

Verify port status: ss -tuln | grep 443

Renew certificates monthly


