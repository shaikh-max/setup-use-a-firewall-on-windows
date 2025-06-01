# setup-use-a-firewall-on-windows
Objective: Configure and test basic firewall rules to allow or block traffic.

Tools Used:

Windows Firewall (Windows 10)

Command Prompt

Steps Performed (Windows):

1. Open Windows Firewall Configuration Tool:

Navigate to Control Panel > System and Security > Windows Defender Firewall.

Click on Advanced settings to open the Windows Firewall with Advanced Security.

2. List Current Firewall Rules:

In the left pane, select Inbound Rules to see current rules applied.

3. Add Rule to Block Port 23 (Telnet):

In the right pane, click on New Rule...

Select Port and click Next.

Choose TCP, specify port 23, then click Next.

Select Block the connection, then click Next.

Apply to all profiles (Domain, Private, Public).

Name the rule (e.g., "Block Telnet") and click Finish.

4. Test Rule Using Telnet:

Telnet client was not recognized initially, so enabled using:

dism /online /Enable-Feature /FeatureName:TelnetClient

Used elevated command prompt (Administrator) to enable it.

Ran the command:

telnet localhost 23

Response: Could not open connection to the host, on port 23: Connect failed

This confirms port 23 is blocked.

5. Add Rule to Allow SSH (Port 22) [If on Linux/UFW]:
On Linux using UFW:

sudo ufw allow 22

6. Remove Block Rule to Restore State:

Go back to Inbound Rules, locate the "Block Telnet" rule, right-click > Delete.

7. Commands/Steps Used Summary:

Open Advanced Firewall

Add Inbound Rule (TCP Port 23, Block)

Enable Telnet Client

Test Telnet Connection

Remove Rule

8. Firewall Filtering Summary:
A firewall filters traffic based on rules defined for incoming/outgoing packets. It acts as a barrier between trusted and untrusted networks, allowing only traffic that meets security criteria. Common filtering parameters include:

Ports (e.g., 22 for SSH, 23 for Telnet)

IP addresses or ranges

Protocols (TCP, UDP)

Application-based rules

