# 🔐 Linux Firewall Configuration Lab (UFW)

## 📘 Overview

This repository documents a hands-on lab to configure and test a firewall using **UFW (Uncomplicated Firewall)** on **Linux (Kali)**. The lab includes blocking and allowing specific ports, testing connectivity with a remote Windows machine, and understanding how firewalls filter network traffic.

---

## 🎯 Objectives

- Enable and manage UFW on a Linux system
- Add rules to allow/deny traffic on specific ports
- Test firewall rules using Telnet from a Windows machine
- Understand how UFW filters incoming traffic

---

## 🛠️ Tools Used

- **Linux (Kali Linux)** with UFW and netcat (`nc`)
- **Windows 10/11** with Telnet client
- LAN connection between Linux and Windows hosts

---

## 📋 Lab Steps

1. Enable UFW and list existing rules
2. Allow port 22 for SSH
3. Deny port 23 to block Telnet
4. Start listener using netcat (`nc`)
5. Attempt connection from Windows via Telnet
6. Observe connection behavior when port is denied/allowed
7. Restore original firewall state

---

## 💻 Key Commands Used

# Linux Terminal
sudo ufw enable
sudo ufw status
sudo ufw allow 22
sudo ufw deny 23
sudo nc -lvp 23
sudo ufw allow 23
sudo ufw delete deny 23

# Windows PowerShell
telnet <Linux-IP> 23
