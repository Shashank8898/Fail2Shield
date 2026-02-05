# SSH-Guard 🔐

**SSH-Guard** is a lightweight, production-ready Bash tool that automatically monitors SSH login attempts, detects brute-force attacks, and blocks malicious IP addresses in real time using UFW.

Built for Linux servers, SSH-Guard runs silently in the background and protects your system 24/7 — no agents, no heavy dependencies, no bloat.

---

## 🚀 Why SSH-Guard?

Most small servers get attacked **within minutes** of going online. Admins often notice only *after* damage is done.

SSH-Guard solves this by:

* Monitoring SSH authentication logs
* Detecting repeated failed login attempts
* Automatically blocking attacker IPs
* Keeping clean, auditable logs

All with a simple Bash-based setup.

---

## ✨ Features

* 🔍 Real-time SSH brute-force detection
* 🚫 Automatic IP blocking via UFW
* ⚙️ Configurable attempt thresholds
* 📝 Detailed logs of blocked IPs
* ⏱️ Cron-ready for full automation
* 🪶 Zero external dependencies

---

## 🧠 How It Works (Simple)

1. Reads `/var/log/auth.log`
2. Extracts failed SSH login attempts
3. Counts attempts per IP
4. Blocks IPs exceeding the configured limit
5. Logs all actions for auditing

---

## 📁 Project Structure

```
ssh-guard/
├── install.sh          # Installer script
├── ssh-guard.sh        # Main security script
├── config.conf         # Configuration file
├── blocked_ips.log     # Blocked IP history
├── alerts.log          # Security alerts
├── uninstall.sh        # Clean removal
└── README.md
```

---

## ⚙️ Configuration

Edit `config.conf`:

```bash
LOG_FILE="/var/log/auth.log"
MAX_ATTEMPTS=5
UFW_ENABLE=true
```

* `MAX_ATTEMPTS` → Number of failed logins before blocking
* `UFW_ENABLE` → Enable/disable firewall blocking

---

## 🛠 Installation

```bash
git clone https://github.com/yourusername/ssh-guard.git
cd ssh-guard
sudo chmod +x install.sh
sudo ./install.sh
```

The installer:

* Verifies UFW
* Sets permissions
* Prepares log files

---

## ⏱️ Automation (Recommended)

Run SSH-Guard every 5 minutes:

```bash
sudo crontab -e
```

Add:

```bash
*/5 * * * * /opt/ssh-guard/ssh-guard.sh
```

---

## 🧪 Testing

Trigger failed SSH attempts:

```bash
ssh fakeuser@localhost
```

After multiple failures, verify:

```bash
sudo ufw status
cat blocked_ips.log
```

---

## 📄 Logs & Auditing

* `blocked_ips.log` → All blocked IPs with timestamps
* `alerts.log` → Security events

Useful for audits and compliance.

---

## 🧑‍💼 Who Is This For?

* VPS & cloud server owners
* Freelancers hosting websites
* Startups without a full-time sysadmin
* Linux administrators

---

## 💼 Commercial Use

SSH-Guard is suitable for **client deployments**, internal servers, and managed services.

You may:

* Install it on client servers
* Bundle it with your sysadmin services
* Customize thresholds per client

---

## 🛡️ Disclaimer

SSH-Guard improves server security but does not replace full security audits, proper key-based authentication, or best practices.

---

## 📬 Support & Customization

Need alerts (Email / Telegram), whitelisting, or temporary bans?

This project is designed to be easily extendable.

---

## ⭐ Final Note

If SSH security matters to you, **SSH-Guard** is a simple tool that just works.

Minimal. Reliable. Secure.
