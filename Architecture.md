# Technical Architecture

### Environment
Deployment was executed on a hardened Debian 12 environment. 

### Network Hardening
Standard network listeners were purged to minimize the attack surface:
- TCP Syncookies: Enabled
- Non-essential services (Exim4, rpcbind): Removed
- SSH: Moved to non-standard port with Key-only authentication.

### Hidden Service Configuration
Tor V3 hidden service mapping via /etc/tor/torrc:
HiddenServiceDir /var/lib/tor/hidden_service/
HiddenServicePort 80 127.0.0.1:8080

### Stealth Proxy Layer
Nginx was configured as a local-only reverse proxy to prevent real-IP disclosure via direct port discovery:
- server_tokens off
- allow 127.0.0.1
- deny all
