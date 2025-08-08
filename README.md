# Task 4: Setup and Use a Firewall on Linux (UFW)

## Objective
To configure and test basic firewall rules using **UFW (Uncomplicated Firewall)** on Linux. This task demonstrates how firewalls manage network traffic and enhance security.

---

## Steps & Explanation

### 1. Open Firewall Configuration Tool
I used **UFW**, a user-friendly front end for managing iptables on Linux systems.

**Command Used:**
```bash
sudo ufw enable
```

### 2. List Current Firewall Rules
Before applying any new rules, I listed all existing rules to check the current configuration.

**Command Used:**
```bash
sudo ufw status numbered
```

### 3. Add a Rule to Block Inbound Traffic on Port 23 (Telnet)
Port 23 is used by Telnet, which is insecure due to its lack of encryption. Blocking this port is a common practice.

**Command Used:**
```bash
sudo ufw deny 23
```

**Screenshot:**
<img width="1000" height="900" alt="Firewall_list_of_port" src="https://github.com/user-attachments/assets/7dfd9af3-2b66-49cb-bd84-9a2650d0ea06" />

### 4. Test the Block Rule
To confirm that port 23 was blocked, I attempted to connect to it.

**Command Used:**
```bash
telnet localhost 23
```

As expected, the connection was refused, proving that the rule worked.

**Screenshot:**
<img width="1000" height="900" alt="connection_test" src="https://github.com/user-attachments/assets/f37f994e-533b-418d-82ae-db6bd029167d" />

### 5. Add Rule to Allow SSH (Port 22)
SSH (port 22) is required for secure remote access.

**Command Used:**
```bash
sudo ufw allow 22
```

### 6. Remove the Telnet Block Rule
After testing, I removed the Telnet block rule to restore the firewall to its original state.

**Command Used:**
```bash
sudo ufw delete deny 23
```

**Screenshot:**
<img width="1000" height="900" alt="update_ufw_for_ssh" src="https://github.com/user-attachments/assets/efb44ac7-1dad-448a-b662-dd74160efa1e" />

## Understanding Firewall Filtering

A **firewall** filters network traffic based on pre-defined rules. It can allow or deny traffic based on:

* **Port numbers** (e.g., 22, 80, 443, etc.)
* **Protocols** (TCP/UDP)
* **IP addresses** (source or destination)

In this task:
* **Blocking port 23** prevented Telnet access (an insecure protocol).
* **Allowing port 22** enabled secure SSH access.
* **Removing the rule** restored network access for port 23.

Firewalls are crucial for:
* Reducing attack surfaces
* Preventing unauthorized access
* Enforcing traffic rules

## Files in This Repo

| File Name | Description |
|-----------|-------------|
| `firewall_list_of_port.png` | Screenshot of existing UFW rules |
| `connection_test.png` | Screenshot of blocked Telnet connection |
| `update_ufw_for_ssh.png` | Screenshot showing SSH rule being added |
| `README.md` | This documentation file |
