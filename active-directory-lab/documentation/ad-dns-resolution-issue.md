# Active Directory – DNS Resolution Issue

## Overview  
User was unable to access domain resources due to incorrect DNS configuration on the client machine.

---

## Symptoms  

- Cannot access domain resources  
- Domain login slow or failing  
- Hostnames not resolving  

![Failed domain access or network error](<insert-failed-access-screenshot-link>)

---

## Environment  

- Domain: Equinox.local  
- Domain Controller: DC01  
- Client: WS01  

![ipconfig showing network configuration](<insert-ipconfig-before-fix-screenshot-link>)

---

## Root Cause  

Client was configured with external DNS instead of internal Domain Controller DNS server.

---

## Investigation Steps  

### 1. Check Network Configuration via GUI  
- Opened Network Connections using `ncpa.cpl`  
- Accessed adapter properties  
- Checked IPv4 settings  

![Network Connections window (ncpa.cpl)](<insert-ncpa-main-window-screenshot-link>)

---

### 2. Verify DNS Configuration  
- Opened IPv4 properties  
- Checked “Use the following DNS server addresses”  

![IPv4 properties showing incorrect DNS (8.8.8.8 or ISP DNS)](<insert-wrong-dns-screenshot-link>)

---

## Resolution Steps  

### 1. Correct DNS Settings  
- Updated DNS to Domain Controller (DC01 IP) via IPv4 settings  

![Correct DNS set to Domain Controller IP](<insert-fixed-dns-screenshot-link>)

---

### 2. Refresh Network Connection  
- Disabled and enabled network adapter  
- Or reconnected network interface  

![Network adapter disabled/enabled status](<insert-reconnect-adapter-screenshot-link>)

---

## Verification  

- Domain resources now accessible  
- Login successful  
- Network stable  

![Successful domain login or ping after fix](<insert-success-verification-screenshot-link>)

---

## Resolution Summary  

The issue was caused by incorrect DNS configuration on the client machine. Updating the DNS settings via Network Adapter Properties (`ncpa.cpl`) to point to the Domain Controller restored domain connectivity.

---

## Prevention  

- Always configure DNS to point to Domain Controller in AD environments  
- Avoid using public DNS (e.g., 8.8.8.8) on domain-joined machines  
- Verify network settings during workstation setup and onboarding
