# Active Directory – DNS Resolution Issue

## Overview  
User was unable to access domain resources due to incorrect DNS configuration on the client machine.

---

## Symptoms  

- Cannot access domain resources  
- Domain login slow or failing  
- Hostnames not resolving  

![Failed domain access or network error](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-006-Cant-connect-to-server.png?raw=true)

---

## Environment  

- Domain: Equinox.local  
- Domain Controller: DC01  
- Client: WS01  

![ipconfig showing network configuration](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-006-DNS.png?raw=true)

---

## Root Cause  

Client was configured with external DNS instead of internal Domain Controller DNS server.

---

## Investigation Steps  

### 1. Check Network Configuration via GUI  
- Opened Network Connections using `ncpa.cpl`  
- Accessed adapter properties  
- Checked IPv4 settings  

![Network Connections window (ncpa.cpl)](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-006-Client-DNS.png?raw=true)

---

### 2. Verify DNS Configuration  
- Opened IPv4 properties  
- Checked “Use the following DNS server addresses”  

---

## Resolution Steps  

### 1. Correct DNS Settings  
- Updated DNS to Domain Controller (DC01 IP) via IPv4 settings  

![Correct DNS set to Domain Controller IP](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-0061-Client-DNS.png?raw=true)

---

### 2. Refresh Network Connection  
- Disabled and enabled network adapter  
- Or reconnected network interface  

---

## Verification  

- Domain resources now accessible  
- Login successful  
- Network stable  

![Successful domain login or ping after fix](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-006-Welcome-Message.png?raw=true)

![Server Login Page](https://github.com/vladimirzeth/IT-Portfolio/blob/main/active-directory-lab/screenshots/HD-AD-006-Can-Login-to-Server.png?raw=true)


---

## Resolution Summary  

The issue was caused by incorrect DNS configuration on the client machine. Updating the DNS settings via Network Adapter Properties (`ncpa.cpl`) to point to the Domain Controller restored domain connectivity.

---

## Prevention  

- Always configure DNS to point to Domain Controller in AD environments  
- Avoid using public DNS (e.g., 8.8.8.8) on domain-joined machines  
- Verify network settings during workstation setup and onboarding
