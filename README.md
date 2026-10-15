# Peer-to-Peer Local Area Network Verification

## 📌 Project Overview

This project demonstrates the configuration and verification of a simple **Peer-to-Peer Local Area Network (LAN)** using **Cisco Packet Tracer**.

Two workstations, **PC0** and **PC1**, are connected through a **Cisco 2960 Layer 2 switch (Switch0)**. Both PCs are configured with static IPv4 addresses in the same subnet (`192.168.10.0/24`). Connectivity is verified using the `ping` command, and the `arp -a` command confirms IP-to-MAC address resolution between the two hosts.

## 🎯 Objective

- To create a basic Local Area Network using Cisco Packet Tracer.
- To connect two PCs through a Layer 2 switch.
- To configure static IPv4 addresses, subnet masks and default gateways.
- To verify end-to-end connectivity using the `ping` command.
- To verify Layer 2 and Layer 3 resolution using the ARP table (`arp -a`).
- To troubleshoot basic connectivity problems.

## 🛠️ Software Used

- Cisco Packet Tracer
- IPv4 Networking

## 🌐 Network Topology

```
 PC0 (192.168.10.25)
      |
      | Fa0/1
 +-----------+
 |  Switch0  |
 |   2960    |
 +-----------+
      | Fa0/2
      |
 PC1 (192.168.10.26)
```

## 📦 Devices Used

| Device | Quantity |
|---|---|
| PC | 2 |
| Cisco 2960 Switch | 1 |
| Copper Straight-Through Cable | 2 |

### IP Address Configuration

| Device | Interface | IPv4 Address | Subnet Mask | Default Gateway | Connected To |
|---|---|---|---|---|---|
| PC0 | FastEthernet0 | 192.168.10.25 | 255.255.255.0 | 192.168.10.1 | Switch0 (Fa0/1) |
| PC1 | FastEthernet0 | 192.168.10.26 | 255.255.255.0 | 192.168.10.1 | Switch0 (Fa0/2) |
| Switch0 | 2960 Series | Unmanaged / Default | — | — | — |

Both PCs belong to the same network: `192.168.10.0/24`

## 🔌 Physical Connections

The devices are connected using **Copper Straight-Through** cables:

- PC0 FastEthernet0 → Switch0 FastEthernet0/1
- PC1 FastEthernet0 → Switch0 FastEthernet0/2

The switch ports change from amber to green after spanning tree converges (about 30 seconds, or use the Fast Forward Time button twice).

## ⚙️ Implementation Procedure

### Step 1: Place the Devices
Add PC0, PC1 and a Cisco 2960 switch to the workspace.

### Step 2: Cable the Network
Select **Connections → Copper Straight-Through** and connect:

- PC0 Fa0 → Switch0 Fa0/1
- PC1 Fa0 → Switch0 Fa0/2

Wait until the link lights turn green.

### Step 3: Configure PC0
PC0 → Desktop → IP Configuration → Static

```
IP Address:       192.168.10.25
Subnet Mask:      255.255.255.0
Default Gateway:  192.168.10.1
```

### Step 4: Configure PC1
PC1 → Desktop → IP Configuration → Static

```
IP Address:       192.168.10.26
Subnet Mask:      255.255.255.0
Default Gateway:  192.168.10.1
```

## 🧪 Verification

### Step 5: Check PC0 Configuration
PC0 → Desktop → Command Prompt

```
ipconfig
```

Verify that PC0 has IP address `192.168.10.25` and subnet mask `255.255.255.0`.

### Step 6: Ping PC1 from PC0

```
ping 192.168.10.26
```

Expected output (the first packet may time out because of ARP resolution):

```
Reply from 192.168.10.26: bytes=32 time<1ms TTL=128
Reply from 192.168.10.26: bytes=32 time<1ms TTL=128
Reply from 192.168.10.26: bytes=32 time<1ms TTL=128
Reply from 192.168.10.26: bytes=32 time<1ms TTL=128
```

### Step 7: Inspect the ARP Table

```
arp -a
```

An entry for `192.168.10.26` must be listed with its MAC address:

```
Internet Address      Physical Address      Type
192.168.10.26         xxxx.xxxx.xxxx        dynamic
```

This confirms complete Layer 2 and Layer 3 resolution.

## 🔍 Troubleshooting

1. **Check the cable:** Use Copper Straight-Through cables (PC to switch).
2. **Check link lights:** Ports should be green. Wait or use Fast Forward Time.
3. **Check IP addresses:** PC0 = `192.168.10.25`, PC1 = `192.168.10.26`.
4. **Check subnet masks:** Both PCs must use `255.255.255.0`.
5. **Check the network:** Both PCs must be in `192.168.10.0/24`.
6. **Run ping before `arp -a`:** The ARP table is empty until a ping is sent.
7. **Retest:** Run `ping 192.168.10.26` again from PC0.



## 📂 Project Files

```
Peer-to-Peer-Local-Area-Network-Verification/
│
├── README.md
├── Peer_to_Peer_LAN.pkt
│
└── screenshots/
    ├── 01_Topology.png
    ├── 02_PC0_IP_Configuration.png
    ├── 03_PC1_IP_Configuration.png
    ├── 04_PC0_ipconfig.png
    ├── 05_Successful_Ping.png
    └── 06_ARP_Table.png
```

## 📚 Concepts Covered

- Local Area Network (LAN)
- IPv4 Addressing
- Static IP Configuration
- Subnet Mask and Default Gateway
- Layer 2 Switch
- FastEthernet
- Copper Straight-Through Cable
- `ipconfig`, `ping` and `arp` commands
- Address Resolution Protocol (ARP)
- Basic Network Troubleshooting

## ✅ Result

A peer-to-peer Local Area Network was successfully created using two PCs and a Cisco 2960 Layer 2 switch. Static IPv4 addresses were configured on both workstations, connectivity was verified using the `ping` command, and the ARP table confirmed the IP-to-MAC mapping of PC1.

## 👨‍💻 Author

SELVALAKSHMI P


Course: B.Tech – Computer Science and Business Systems
