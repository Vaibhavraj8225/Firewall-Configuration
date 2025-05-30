Objective
Configure and test basic firewall rules using UFW on Linux to allow and block traffic on specific ports. Verify firewall behavior using a Windows machine to simulate external connections.
________________________________________
Tools Used
•	Linux (Kali Linux) : UFW firewall, netcat (nc)
•	Windows 10/11 : Command Prompt with Telnet client
•	Network setup : Both machines on the same LAN
________________________________________
Steps and Commands
1. Enable the Firewall and View Current Rules

sudo ufw enable
sudo ufw status
________________________________________
2. Allow SSH Traffic on Port 22 (for remote access)


sudo ufw allow 22
________________________________________
3. Deny Inbound Traffic on Port 23 (Telnet)


sudo ufw deny 23
________________________________________
4. Verify Firewall Rules


sudo ufw status verbose
________________________________________
5. Start a Listener on Port 23 (Linux Terminal)


sudo nc -lvp 23
________________________________________
6. From Windows, Attempt to Connect via Telnet
powershell

telnet <Kali-IP> 23
•	Expected: Connection is refused or fails (blocked by firewall).
________________________________________
7. Modify Rule to Allow Port 23


sudo ufw allow 23
________________________________________
8. Retest the Telnet Connection from Windows
powershell

telnet <Kali-IP> 23
•	Expected: Connection is successful.
________________________________________
9. Clean Up (Optional)


sudo ufw delete deny 23
________________________________________
Screenshots
Screenshot 1 — Blocking Test (Port 23 Denied)
![Image](https://github.com/user-attachments/assets/25072f0a-9ed5-4253-a799-b99ec31d36fe)
Includes:
•	Linux terminal showing:
o	sudo ufw enable
o	sudo ufw status
o	sudo ufw deny 23
o	sudo nc -lvp 23
•	Windows PowerShell:
o	telnet <Kali-IP> 23 showing connection refused
________________________________________
Screenshot 2 — Allowing Test (Port 23 Allowed)
![Image](https://github.com/user-attachments/assets/7809437e-c7cf-4e1f-87b8-89a9ee7bac0f)
Includes:
•	Linux terminal showing:
o	sudo ufw allow 23
o	sudo nc -lvp 23
•	Windows PowerShell:
o	telnet <Kali-IP> 23 showing connected
________________________________________

Screenshot 3 — Applying Deny Rule on Port 23
![Image](https://github.com/user-attachments/assets/3509553d-c49a-4d84-93ac-392ce1616e5e)
Shows:
•	Linux terminal explicitly running:
o	sudo ufw deny 23
•	Confirms the deny rule has been added
________________________________________
Summary: How UFW Filters Traffic
UFW (Uncomplicated Firewall) is a front-end to iptables that simplifies firewall rule management. It filters incoming and outgoing traffic based on rules that match protocols and port numbers.
•	Default Policy: Deny all incoming, allow all outgoing.
•	Rules: You can allow or deny specific ports or IPs.
•	Loopback Traffic: UFW does not block localhost (127.0.0.1) by default.
•	Verification: External machine (Windows) used to simulate real network traffic for proper firewall testing.
________________________________________
Learning Outcome
You have successfully:
•	Enabled and managed firewall rules using UFW
•	Blocked and allowed specific ports
•	Validated rule enforcement using external Telnet testing
•	Understood UFW's behavior with loopback vs. external traffic
•	Verified rule effectiveness using an external Windows host
•	 Demonstrated understanding of how firewalls control traffic flow


