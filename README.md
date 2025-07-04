# V2Ray-X-UI
X-UI, a multi-user Xray graphical management panel (replacing V2-UI and V2Ray)



X-UI provides a graphical user interface for managing servers and users. You can visually build servers for Shadowsocks, V2ray, Xray, Trojan, and other popular protocols. You can also monitor VPS performance and traffic usage in real time. X-UI replaces the older V2-UI panel.

Preparation
Before you begin, you need to do three or four things:

Get a virtual private server or VPS. You can get a VPS from many providers. Some popular ones are AWS, Google Cloud, Microsoft Azure, DigitalOcean, Hetzner, and Vultr. In our example we use a Debian 11 VPS, but the X-UI install script supports Ubuntu 16+, Debian 8+, or CentOS 7+. You need to have ports 80 and 443 on your VPS open for TCP input. Also open port 54321 for TCP input.
Get a domain name. Some low-cost registrars are Porkbun, Namesilo, and Namecheap.
Create a DNS A record pointing from your host name to your VPS.
Optionally, add your domain to Cloudflare. This will allow you to insert a content distribution network or CDN in between you and your server. However, if you are going to add a CDN, do not turn on proxying in Cloudflare until the end. For now, just use the DNS features of Cloudflare. Adding your domain to Cloudflare is optional, and you can continue to use your domain name registrar’s nameservers if you prefer. In any case, not all protocols support the use of CDN proxying.




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


