# Active Directory – DNS Resolution Issue

## Overview  
User was unable to access domain resources due to incorrect DNS configuration on the client machine.

---

## Symptoms  

- Cannot access domain resources  
- Domain login slow or failing  
- Hostnames not resolving  

![Failed domain access or ping error](<insert-failed-access-screenshot-link>)

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

### 1. Check IP Configuration  
- Ran `ipconfig /all`  
- Verified DNS settings  

![ipconfig showing incorrect DNS (8.8.8.8 or ISP DNS)](<insert-wrong-dns-screenshot-link>)

---

### 2. Verify Name Resolution  
- Ran `nslookup equinox.local`  
- Confirmed resolution failure  

![nslookup failure output](<insert-nslookup-failure-screenshot-link>)

---

## Resolution Steps  

### 1. Fix DNS Configuration  
- Set DNS server to Domain Controller (DC01 IP)

![DNS settings corrected to Domain Controller IP](<insert-fixed-dns-screenshot-link>)

---

### 2. Flush DNS Cache  
- Ran `ipconfig /flushdns`  

---

### 3. Restart Network Adapter  
- Disabled and re-enabled network adapter  

---

## Verification  

- Domain resources now accessible  
- DNS resolution working  
- Login successful  

![Successful ping or domain login after fix](<insert-success-verification-screenshot-link>)

---

## Resolution Summary  

Client DNS was corrected from external DNS to internal Domain Controller DNS, restoring domain connectivity and authentication.

---

## Prevention  

- Always configure DNS to point to Domain Controller in AD environments  
- Avoid using public DNS on domain-joined machines  
- Verify DNS settings during workstation setup
