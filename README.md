# 🔐 VPN Connectivity & Security Demonstration — ProtonVPN on Linux

Virtual Private Networks (VPNs) help protect online privacy, secure traffic over public networks, and mask your IP by routing traffic through encrypted tunnels.  
In this practical, I installed and configured **ProtonVPN CLI** on Parrot OS to demonstrate secure connectivity.

---

## 🎯 Objective

- Install ProtonVPN CLI on Parrot OS  
- Authenticate and securely connect to a VPN server  
- Verify IP address change and encrypted tunnel  
- Capture logs & screenshots  
- Document procedure for cyber labs/internship use

---

## 🖥️ Environment Used

| Component | Details |
|---|---|
OS | Parrot OS (Debian-based) |
VPN Tool | ProtonVPN CLI |
Privileges Required | Sudo |
Verification | IP lookup + DNS check |
Outcome | ✅ VPN successfully installed & connected |

---

## ⚙️ Step 1 — Update & Prepare System

First, updated system packages and installed essential dependencies:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y wget apt-transport-https gnupg lsb-release
````

> 📷 *Screenshot: Package update completed*

---

## 📦 Step 2 — Add ProtonVPN Repository

Download and install official repository:

```bash
wget https://repo.protonvpn.com/debian/dists/stable/main/binary-all/protonvpn-stable-release_1.0.8_all.deb
sudo dpkg -i protonvpn-stable-release_1.0.8_all.deb
sudo apt update
```

> 📷 *Screenshot: ProtonVPN repo added*

---

## 🛠️ Step 3 — Install ProtonVPN CLI

Installed using pipx:

```bash
sudo apt install -y pipx
pipx install protonvpn-cli
```

> 📷 *Screenshot: ProtonVPN CLI installed*

---

## 🔍 Step 4 — Verify Installation Path

Check binary location:

```bash
which protonvpn-cli
```

If not detected, locate manually:

```bash
find ~/.local/bin -name "protonvpn*" 2>/dev/null
```

Expected output (example):

```
/home/user/.local/bin/protonvpn-cli
```

> 📷 *Screenshot: Binary path found*

---

## 🌐 Step 5 — Add VPN Executable System-Wide

Create symbolic link to global path:

```bash
sudo ln -s ~/.local/bin/protonvpn-cli /usr/local/bin/protonvpn-cli
```

Verify version:

```bash
protonvpn --version
```

Expected:

```
ProtonVPN v2.2.11
```

> 📷 *Screenshot: Version check output*

---

## 🔧 Step 6 — Initialize ProtonVPN

Run setup:

```bash
sudo protonvpn init
```

Configurations chosen:

| Option   | Value                 |
| -------- | --------------------- |
| Protocol | UDP (faster for VPN)  |
| DNS      | ProtonDNS             |
| Plan     | Free Plan             |
| Server   | Any available country |

> 📷 *Screenshot: ProtonVPN initialization*

---

## 🔑 Step 7 — Login to ProtonVPN

Use ProtonVPN account credentials:

```bash
sudo protonvpn-cli login YOUR_USERNAME
```

> 📷 *Screenshot: Successful login*

---

## 🔗 Step 8 — Connect to VPN

Auto-select fastest free server:

```bash
sudo protonvpn-cli connect --fastest
```

Disconnect when needed:

```bash
sudo protonvpn-cli disconnect
```

---

## 🔎 Step 9 — Verify VPN Connection

### ✅ Check new IP:

```bash
curl ifconfig.me
```

### ✅ Check DNS:

```bash
nslookup google.com
```

### ✅ Confirm routing:

```bash
ip route
```

> 📷 *Screenshot: IP before & after VPN connection*

Expected behavior:

* IP changes to VPN server location
* DNS using ProtonDNS
* Traffic routed through encrypted tunnel

---

## 🛡️ Security Benefits Observed

| Security Feature        | Explanation                |
| ----------------------- | -------------------------- |
| Encrypted tunnel 🔐     | Protects data in transit   |
| IP masking 🌍           | Hides real location        |
| DNS Leak protection 🛑  | ProtonDNS prevents leakage |
| Safe on public Wi-Fi 📴 | Blocks sniffing attacks    |

---

## 📊 Observations

* ProtonVPN successfully connected & encrypted traffic ✅
* IP & DNS changed confirming secure tunnel ✅
* Internet speed stable (minor latency expected) ✅

---

## ✅ Conclusion

This practical demonstrated how to securely install and use ProtonVPN on Linux.
VPN ensured encrypted browsing, protected privacy, and verified traffic anonymity.

> **VPNs are essential for cybersecurity professionals to maintain secure communication channels and privacy online.**

---


## 🪪 Note

This project is for educational & cybersecurity learning use only.

