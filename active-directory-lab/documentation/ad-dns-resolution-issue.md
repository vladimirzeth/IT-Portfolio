# Active Directory – DNS Resolution Issue

## Overview  
User was unable to access domain resources due to incorrect DNS configuration on the client machine.

---

## Symptoms  

- Cannot access domain resources  
- Domain login slow or failing  
- Hostnames not resolving  

📸 **Screenshot 1: Error or failure evidence**
> Capture:  
- Failed domain login OR  
- “Server not found / cannot reach domain” message  
- OR ping failure to domain (if applicable)

Example commands to show:
- `ping dc01`
- `ping equinox.local`

---

## Environment  

- Domain: Equinox.local  
- Domain Controller: DC01  
- Client: WS01  

📸 **Screenshot 2: Network configuration baseline**
> Capture:
- `ipconfig /all` output showing:
  - DNS server (IMPORTANT)
  - IP address
  - Gateway

👉 This proves wrong DNS configuration

---

## Root Cause  

Client was configured with external DNS instead of internal Domain Controller DNS server.

---

## Investigation Steps  

### 1. Check IP Configuration  

- Ran `ipconfig /all`  
- Verified DNS settings  

📸 **Screenshot 3: Evidence of wrong DNS**
> Capture clearly:
- DNS servers showing:
  - ❌ 8.8.8.8 / external DNS  
  - ❌ ISP DNS  
- This is your “AHA MOMENT” screenshot

---

### 2. Verify Name Resolution  

- Ran `nslookup equinox.local`  
- Confirmed resolution failure  

📸 **Screenshot 4: DNS failure proof**
> Capture:
- nslookup output failing OR
- “Non-existent domain” / timeout result

---

## Resolution Steps  

### 1. Fix DNS Configuration  
- Set DNS server to Domain Controller (DC01 IP)

📸 **Screenshot 5: Fix applied**
> Capture:
- Network adapter IPv4 settings showing:
  - Preferred DNS = DC01 IP

---

### 2. Flush DNS Cache  
- Ran: `ipconfig /flushdns`  

📸 (Optional Screenshot 6)
> Capture command execution (proof of remediation step)

---

### 3. Restart Network Adapter  
- Disabled and enabled adapter OR restarted system  

📸 (Optional Screenshot 7)
> Capture:
- Network reconnect OR
- Successful reconnect status

---

## Verification  

- Domain resources now accessible  
- DNS resolution working  
- Login successful  

📸 **Screenshot 8: Final proof (VERY IMPORTANT)**
> Capture ONE of the following:
- Successful `ping dc01`
- Successful domain login
- Successful `nslookup equinox.local`

👉 This is your “issue fully resolved” proof

---

## Resolution Summary  

Client DNS was corrected from external DNS to internal Domain Controller DNS, restoring domain connectivity and authentication.

---

## Prevention  

- Always set DNS to Domain Controller in AD environments  
- Avoid using public DNS in domain-joined machines  
- Validate DNS settings during onboarding  
