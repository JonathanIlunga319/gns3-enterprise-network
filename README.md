# 🌐 GNS3 Enterprise Network Project

A full enterprise network simulation built in GNS3 connecting a **Bank**, **School**, **Hospital**, and **3 Homes** using Cisco 7200 Routers.

---

## 📋 Project Overview

| Feature | Details |
|---|---|
| Routing Protocol | OSPF (Area 0 Backbone) |
| Devices | Cisco 7200 Routers + Layer 2 Switches |
| Services | DHCP, DNS, VLANs, NAT/PAT, ACL Firewall, VPN (IPSec) |
| Sites | Bank, School, Hospital, Home1, Home2, Home3, Core ISP |

---

## 🗺️ Network Topology

```
                        [CORE-ISP-R]
                        10.0.0.0/30
              __________|___________|___________
             |           |          |           |
         [BANK-R]   [SCHOOL-R]  [HOSP-R]   [HOME-R1]
                                            [HOME-R2]
                                            [HOME-R3]
```

---

## 📁 Project Structure

```
gns3-project/
├── README.md
├── docs/
│   ├── ip-addressing-plan.md
│   ├── vlan-plan.md
│   └── services-overview.md
├── configs/
│   ├── core-isp/
│   │   └── CORE-ISP-R.txt
│   ├── bank/
│   │   ├── BANK-R.txt
│   │   └── BANK-SW.txt
│   ├── school/
│   │   ├── SCHOOL-R.txt
│   │   └── SCHOOL-SW.txt
│   ├── hospital/
│   │   ├── HOSP-R.txt
│   │   └── HOSP-SW.txt
│   ├── home1/
│   │   └── HOME1-R.txt
│   ├── home2/
│   │   └── HOME2-R.txt
│   └── home3/
│       └── HOME3-R.txt
└── diagrams/
    └── topology-description.md
```

---

## 🚀 How to Use in GNS3

1. Open GNS3 and create a new project
2. Add **Cisco 7200 Routers** for each site
3. Add **Ethernet switches** for LAN segments
4. Connect devices as per the topology diagram
5. Copy each config from `configs/` folder into the router console
6. Verify with `show ip ospf neighbor` and `ping` tests

---

## 🔐 Security Features

- **ACL Firewalls** on Bank and Hospital routers
- **IPSec VPN** tunnels between Bank ↔ Hospital and Bank ↔ School
- **NAT/PAT** on all site routers for internet simulation
- **VLAN segmentation** isolates departments within each site

---

## 📡 OSPF Design

- All sites in **Area 0** (single area OSPF)
- Core ISP router is the **DR (Designated Router)**
- Loopback interfaces used as **Router IDs**

---

## ✅ Verification Commands

```bash
show ip ospf neighbor          # Check OSPF adjacencies
show ip route ospf             # View OSPF learned routes
show ip nat translations       # Verify NAT/PAT
show crypto isakmp sa          # Check VPN Phase 1
show crypto ipsec sa           # Check VPN Phase 2
show vlan brief                # Verify VLANs (on switches)
ping <destination> source <local-ip>   # Test connectivity
```

---

## 👤 Author

Built with Claude AI as a GNS3 learning project.
