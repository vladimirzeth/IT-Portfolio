# Active Directory – RDP Connection Failure

## Overview  
User was unable to connect to a remote machine via Remote Desktop Protocol (RDP).

---

## Symptoms  

- Remote Desktop connection fails  
- Error: “Remote Desktop can't connect to the remote computer”  
- Unable to access remote workstation  

![RDP connection error message](<INSERT SCREENSHOT: RDP ERROR>)

---

## Environment  

- Domain: Equinox.local  
- Domain Controller: DC01  
- Client: WS01  

![System properties showing computer name/domain](<INSERT SCREENSHOT: SYSTEM INFO>)

---

## Root Cause  

Remote Desktop was disabled on the target machine and firewall rules were blocking inbound RDP connections.

---

## Investigation Steps  

### 1. Verify Network Connectivity  
- Pinged target machine using hostname and IP address  
- Confirmed network communication is working  

![Ping result showing connectivity](<INSERT SCREENSHOT: PING SUCCESS>)

---

### 2. Check Remote Desktop Settings  
- Opened System Properties (`sysdm.cpl`)  
- Navigated to Remote tab  
- Found that Remote Desktop was disabled  

![Remote Desktop disabled](<INSERT SCREENSHOT: RDP DISABLED>)

---

### 3. Check Windows Firewall Rules  
- Opened Windows Defender Firewall  
- Verified that Remote Desktop rule was disabled  

![Firewall blocking RDP](<INSERT SCREENSHOT: FIREWALL BLOCK>)

---

## Resolution Steps  

### 1. Enable Remote Desktop  
- Opened System Properties (`sysdm.cpl`)  
- Enabled “Allow remote connections to this computer”  

![Enable Remote Desktop](<INSERT SCREENSHOT: ENABLE RDP>)

---

### 2. Allow RDP Through Firewall  
- Opened Windows Defender Firewall  
- Enabled Remote Desktop rules  

![Allow RDP in firewall](<INSERT SCREENSHOT: FIREWALL ALLOW>)

---

### 3. Add User to Remote Desktop Group  
- Opened Computer Management  
- Navigated to Local Users and Groups  
- Added user to “Remote Desktop Users” group  

![Add user to RDP group](<INSERT SCREENSHOT: ADD USER GROUP>)

---

## Verification  

- Successfully connected via Remote Desktop  
- User able to log in to remote system  

![Successful RDP login](<INSERT SCREENSHOT: SUCCESSFUL RDP>)

---

## Resolution Summary  

The issue was caused by Remote Desktop being disabled and firewall rules blocking RDP traffic. Enabling Remote Desktop and allowing it through the firewall resolved the issue.

---

## Prevention  

- Ensure Remote Desktop is enabled on required systems  
- Configure firewall rules for RDP during system setup  
- Add authorized users to Remote Desktop Users group  
- Regularly verify remote access configurations  
