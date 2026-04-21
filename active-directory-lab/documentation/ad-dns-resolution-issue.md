# Active Directory – DNS Resolution Issue

## Overview  
User was unable to access domain resources due to incorrect DNS configuration on the client machine.

---

## Symptoms  
- Cannot access domain resources  
- Domain login slow or failing  
- Hostnames not resolving  

---

## Environment  
- Domain: Equinox.local  
- Domain Controller: DC01  
- Client: WS01  

---

## Root Cause  
Client was configured with external DNS instead of internal AD DNS server.

---

## Investigation Steps  
- Checked IP configuration using `ipconfig /all`  
- Verified DNS server entries  
- Ran `nslookup Equinox.local`  
- Confirmed resolution failure  

---

## Resolution Steps  
- Set DNS to DC01 IP address  
- Flushed DNS cache (`ipconfig /flushdns`)  
- Restarted network adapter  

---

## Verification  
- Domain resources accessible  
- DNS resolving correctly  
