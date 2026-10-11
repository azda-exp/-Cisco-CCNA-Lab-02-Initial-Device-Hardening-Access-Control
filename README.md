# -Cisco-CCNA-Lab-02-Initial-Device-Hardening-Access-Control
> "Security through obscurity is not security, but plaintext passwords like `cisco` and `lab`? That's just asking for trouble." — *Every SOC Analyst ever.*

[![Cisco IOS](https://img.shields.io/badge/Cisco-IOS-1ba1f2?style=for-the-badge&logo=cisco&logoColor=white)](https://www.cisco.com)
[![Network Security](https://img.shields.io/badge/Lab-Initial_Config-success?style=for-the-badge)](https://packettracerlab.com/ccna-labs/)
[![Status](https://img.shields.io/badge/Status-Completed-informational?style=for-the-badge)]()

---

## 📋 Lab Overview

Welcome to **Lab 02**, where we transition from default factory settings to basic administrative control and management hardening on Cisco IOS devices (`R1` router and `SW1` switch). 

While these credentials are purely academic and insecure for production environments, establishing proper hostname identification, privileged execution access, and line security is the fundamental building block for every serious network engineer and cybersecurity operator.

---

## 🛠️ Topology & Components

- **Devices**: 
  - `R1` (Cisco Router)
  - `SW1` (Cisco Switch)
- **Management Access Points**:
  - Console Line (`con 0`)
  - Auxiliary Line (`aux 0`)
  - Virtual Terminal Lines (`vty`)

---

## 🎯 Lab Objectives & Configuration Tasks

### 1. Router Tasks (`R1`)
- [x] Configure device hostname: `R1`
- [x] Set non-encrypted enable password: `cisco`
- [x] Set encrypted privileged EXEC secret: `cisco`
- [x] Secure console access with password: `lab` (and enable login)
- [x] Secure auxiliary line access with password: `ciscolab` (and enable login)

### 2. Switch Tasks (`SW1`)
- [x] Configure device hostname: `SW1`
- [x] Set non-encrypted enable password: `cisco`
- [x] Set encrypted privileged EXEC secret: `cisco`
- [x] Secure console access with password: `lab` (and enable login)
- [x] Secure auxiliary line access with password: `ciscolab` (and enable login)

---

## 💻 Configuration Scripts

### Router (`R1`) Configuration Snapshot
```ios
R1> enable
R1# configure terminal
R1(config)# hostname R1
R1(config)# enable password cisco
R1(config)# enable secret cisco
R1(config)# line con 0
R1(config-line)# password lab
R1(config-line)# login
R1(config-line)# exit
R1(config)# line aux 0
R1(config-line)# password ciscolab
R1(config-line)# login
R1(config-line)# exit

Switch (SW1) Configuration Snapshot

        

ios
SW1> enable
SW1# configure terminal
SW1(config)# hostname SW1
SW1(config)# enable password cisco
SW1(config)# enable secret cisco
SW1(config)# line con 0
SW1(config-line)# password lab
SW1(config-line)# login
SW1(config-line)# exit
SW1(config)# line aux 0
SW1(config-line)# password ciscolab
R1(config-line)# login
SW1(config-line)# exit

🔍 Verification & Testing

To verify that the running configuration matches the task constraints:

        

ios
R1# show running-config

Check for:

    Correct hostnames (R1, SW1).
    Presence of both enable password and enable secret hashes.
    Active login command under line con 0 and line aux 0.

⚠️ Security Disclaimer

    Note for Future SOC Analysts: Never use cisco, admin, or lab as credentials in a live network environment. Always enforce AAA (Authentication, Authorization, and Accounting) via TACACS+/RADIUS and use strong asymmetric keys or SSH instead of plain Telnet/Console where applicable.

👤 Author

EHSAN SALEHI

    Network Engineering & Cybersecurity Enthusiast
    GitHub Profile
