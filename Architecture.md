# Technical Architecture

### Environment
The simulation was executed on a hardened Debian 12 (Bookworm) environment. A minimal installation was used to reduce the potential attack surface.

### Step 1: Gateway Hardening
To prevent server fingerprinting and mitigate common network-layer attacks, the following modifications were applied to the base OS:

```bash
# Removing non-essential network services
apt-get purge -y exim4 rpcbind 

# Hardening the network stack via sysctl
cat <<EOF >> /etc/sysctl.conf
net.ipv4.tcp_syncookies = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.tcp_rfc1337 = 1
EOF
sysctl -p
```
Step 2: Hidden Service Configuration
We mapped the simulated marketplace to a Tor Version 3 address. The configuration ensures that the backend service is only accessible via the Tor circuit.
```bash
# Edit /etc/tor/torrc
HiddenServiceDir /var/lib/tor/hidden_service/
HiddenServicePort 80 127.0.0.1:8080
```
After restarting Tor, the hostname was retrieved from ``` /var/lib/tor/hidden_service/hostname.```
Step 3: Nginx Stealth Layer
The web server was configured to operate as a local-only reverse proxy. Identifying headers were stripped to prevent server-side metadata leakage.
```server {
    listen 127.0.0.1:8080;
    server_tokens off; 

    # Preventing clickjacking and MIME-type sniffing
    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-Content-Type-Options "nosniff";

    # Restricting access to local loopback only
    allow 127.0.0.1;
    deny all;

    location / {
        # Proxy to simulated marketplace backend
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
    }
}
```
