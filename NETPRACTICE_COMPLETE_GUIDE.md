<div align="center">

# 🌐 NetPractice: The Complete IP Networking Guide

### *From ARPANET to Subnets — Master Networking From First Principles*

[![42 School](https://img.shields.io/badge/42-School-000000?style=for-the-badge&logo=42&logoColor=white)](https://42.fr)
[![Made with Love](https://img.shields.io/badge/Made%20with-Love-ff69b4?style=for-the-badge)](https://github.com)
[![IPv4](https://img.shields.io/badge/Protocol-IPv4-blue?style=for-the-badge)](https://en.wikipedia.org/wiki/IPv4)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

<img src="https://upload.wikimedia.org/wikipedia/commons/d/d2/Internet_map_1024.jpg" width="600" alt="Internet Visualization">

*Visualization of Internet routing paths - Wikimedia Commons*

---

**🎯 One Mission:** Teach you how to make machines talk to each other using correct addresses and routes.

</div>

---

## 📚 Table of Contents

<details>
<summary><strong>Click to expand full table of contents</strong></summary>

### Part I: Foundation — Understanding the Internet
- [1. The Origin Story: Before the Internet](#1-the-origin-story-before-the-internet)
  - [1.1 The Problem That Started Everything](#11-the-problem-that-started-everything)
  - [1.2 ARPANET: The First Network](#12-arpanet-the-first-network)
  - [1.3 The IMP: Grandfather of the Router](#13-the-imp-grandfather-of-the-router)
  - [1.4 From NCP to TCP/IP](#14-from-ncp-to-tcpip)

### Part II: The Binary Foundation
- [2. Why Binary? The Light Bulb Revelation](#2-why-binary-the-light-bulb-revelation)
  - [2.1 The Constraint That Changed Everything](#21-the-constraint-that-changed-everything)
  - [2.2 Power of 2: The Multiplication Discovery](#22-power-of-2-the-multiplication-discovery)
  - [2.3 The Birth of the Byte](#23-the-birth-of-the-byte)
  - [2.4 From Bits to IP Addresses](#24-from-bits-to-ip-addresses)

### Part III: IP Addressing — The City Metaphor
- [3. The 10-Floor Tower of Networking](#3-the-10-floor-tower-of-networking)
- [4. IP Addresses: Your Digital House Number](#4-ip-addresses-your-digital-house-number)
  - [4.1 What Is an IP Address?](#41-what-is-an-ip-address)
  - [4.2 Network vs Host: Street vs House](#42-network-vs-host-street-vs-house)
  - [4.3 Reserved & Special Addresses](#43-reserved--special-addresses)
  - [4.4 Private vs Public IP Ranges](#44-private-vs-public-ip-ranges)

### Part IV: Subnet Masks — The Neighborhood Fence
- [5. Subnet Masks Explained](#5-subnet-masks-explained)
  - [5.1 What Is a Subnet Mask?](#51-what-is-a-subnet-mask)
  - [5.2 The AND Operation: How Computers Calculate Networks](#52-the-and-operation-how-computers-calculate-networks)
  - [5.3 CIDR Notation: The Network Engineer's Shorthand](#53-cidr-notation-the-network-engineers-shorthand)
  - [5.4 The Class System (Historical Context)](#54-the-class-system-historical-context)

### Part V: Subnetting Mathematics
- [6. The Three Calculation Methods](#6-the-three-calculation-methods)
  - [6.1 Method 1: Magic Number (Fastest)](#61-method-1-magic-number-fastest)
  - [6.2 Method 2: Block Size Calculation](#62-method-2-block-size-calculation)
  - [6.3 Method 3: Binary AND (Most Accurate)](#63-method-3-binary-and-most-accurate)
- [7. Complete CIDR Reference Table](#7-complete-cidr-reference-table)

### Part VI: Network Devices
- [8. Hub, Switch, Router: The Evolution](#8-hub-switch-router-the-evolution)
  - [8.1 Hub: The Dead Megaphone](#81-hub-the-dead-megaphone)
  - [8.2 Switch: The Smart Mailman](#82-switch-the-smart-mailman)
  - [8.3 Router: The Border Checkpoint](#83-router-the-border-checkpoint)

### Part VII: Routing
- [9. Routing Tables: The GPS of Networks](#9-routing-tables-the-gps-of-networks)
  - [9.1 Understanding Routing Tables](#91-understanding-routing-tables)
  - [9.2 Default Routes](#92-default-routes)
  - [9.3 Local vs Remote Delivery](#93-local-vs-remote-delivery)

### Part VIII: NAT & DHCP
- [10. NAT: One Public IP, Many Devices](#10-nat-one-public-ip-many-devices)
- [11. DHCP: The Hotel Check-In System](#11-dhcp-the-hotel-check-in-system)

### Part IX: NetPractice Levels
- [Level 1: The Family Network](#level-1-the-family-network)
- [Level 2-10: Progressive Challenges](#level-2-10-progressive-challenges)

### Part X: Quick Reference
- [Cheat Sheets](#cheat-sheets)
- [Common Mistakes](#common-mistakes)
- [Resources & Further Reading](#resources--further-reading)

</details>

---

# Part I: Foundation — Understanding the Internet

## 1. The Origin Story: Before the Internet

> *"You can't invent the solution before experiencing the problem."*

### 1.1 The Problem That Started Everything

**The Year:** 1960s  
**The Frustration:** Researchers at universities across America were doing groundbreaking work, but they couldn't share their findings efficiently.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        THE DARK AGES OF COMPUTING                        │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   MIT ════════════════════════════════════════════════════════ UCLA     │
│    │                                                              │      │
│    │   📼 Ship magnetic tapes by mail (takes WEEKS!)             │      │
│    │   📞 Read results over phone (error-prone!)                 │      │
│    │   🚗 Drive to share data (expensive!)                       │      │
│    │                                                              │      │
│    └──────────────────────────────────────────────────────────────┘      │
│                                                                          │
│   "There HAS to be a better way..." — Every researcher, 1960s           │
└─────────────────────────────────────────────────────────────────────────┘
```

### 1.2 ARPANET: The First Network

**ARPANET** = **A**dvanced **R**esearch **P**rojects **A**gency **Net**work

In 1969, the U.S. Department of Defense funded a revolutionary idea: **connect computers over phone lines**.

```
                         ┌─────────────────────────────────────────┐
                         │           ARPANET - October 1969        │
                         │              (4 Nodes)                   │
                         └─────────────────────────────────────────┘

                                    ┌─────────┐
                                    │   SRI   │
                                    │ Stanford│
                                    └────┬────┘
                                         │
                    ┌─────────┐          │          ┌─────────┐
                    │  UCLA   │──────────┼──────────│  UCSB   │
                    │   LA    │          │          │ Barbara │
                    └─────────┘          │          └─────────┘
                                         │
                                    ┌────┴────┐
                                    │  Utah   │
                                    │   SLC   │
                                    └─────────┘

              First message sent: "LO" (crashed before "LOGIN" completed!)
```

**Key Dates:**
| Year | Event |
|------|-------|
| 1969 | First ARPANET connection (4 nodes) |
| 1971 | Email invented by Ray Tomlinson |
| 1973 | First international connections (UK, Norway) |
| 1983 | TCP/IP becomes mandatory protocol |
| 1990 | ARPANET decommissioned, Internet takes over |

### 1.3 The IMP: Grandfather of the Router

**IMP** = **I**nterface **M**essage **P**rocessor

The **problem**: Computers spoke electricity. Phone lines spoke sound (audio signals).

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     THE TRANSLATION PROBLEM                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│    COMPUTER                                              PHONE LINE     │
│    ┌───────┐                                            ┌───────────┐   │
│    │ 10110 │  ←── Electricity (ON/OFF) ──→ Sound waves │ ~~~~~~~~~~~~│  │
│    │ 01001 │     CAN'T TRAVEL ON COPPER DIRECTLY!      │ ~~~~~~~~~~~~│  │
│    └───────┘                                            └───────────┘   │
│                                                                          │
│                      ⬇️  SOLUTION: THE IMP  ⬇️                           │
│                                                                          │
│    COMPUTER ──→ [IMP] ──→ PHONE LINE ──→ [IMP] ──→ COMPUTER             │
│                  │                           │                           │
│                  └── Translates electricity  │                           │
│                      into musical tones! ────┘                           │
│                                                                          │
│    The IMP is the great-grandfather of your modern ROUTER!              │
└─────────────────────────────────────────────────────────────────────────┘
```

**The IMP's Job:**
1. **Receive** digital data from the computer
2. **Convert** to audio tones (modem-style)
3. **Send** over phone lines
4. **Receive** audio from other IMPs
5. **Convert** back to digital data
6. **Deliver** to destination computer

### 1.4 From NCP to TCP/IP

The first protocol was **NCP** (Network Control Protocol). It worked, but had fatal flaws:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        WHY NCP FAILED                                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  NCP Problems:                           TCP/IP Solutions:              │
│  ───────────────                         ─────────────────              │
│  ❌ No error recovery                    ✅ Guaranteed delivery         │
│  ❌ No congestion control                ✅ Flow control                 │
│  ❌ Single network only                  ✅ Inter-network communication │
│  ❌ Fixed packet sizes                   ✅ Flexible packet sizes       │
│                                                                          │
│  The Lesson: You can't invent the solution before experiencing          │
│              the problem. NCP taught us what broke, TCP/IP fixed it.    │
└─────────────────────────────────────────────────────────────────────────┘
```

**RFC (Request for Comments)**: A place where engineers discuss how the internet should work. All internet standards are documented in RFCs at [rfc-editor.org](https://www.rfc-editor.org/).

---

# Part II: The Binary Foundation

## 2. Why Binary? The Light Bulb Revelation

### 2.1 The Constraint That Changed Everything

**The Year:** 1940s  
**The Frustration:** Engineers needed to store numbers, but they only had electricity to work with.

**The Constraint:**
```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE ONLY TWO STATES OF ELECTRICITY                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│         💡 OFF = 0                          💡 ON = 1                    │
│                                                                          │
│         Light bulb: OFF or ON                                           │
│         Switch: DOWN or UP                                              │
│         Voltage: LOW or HIGH                                            │
│                                                                          │
│    "How do we count and store numbers when we only have ON/OFF?"        │
└─────────────────────────────────────────────────────────────────────────┘
```

**The Breakthrough Question:**  
*"What if we used MULTIPLE switches to represent larger numbers?"*

### 2.2 Power of 2: The Multiplication Discovery

**With ONE light bulb:**
```
💡 OFF = 0
💡 ON  = 1

Answer: 2 values (0 and 1)
```

**With TWO light bulbs:**
```
Bulb 1    Bulb 2    Value
───────   ───────   ─────
  OFF       OFF       0
  OFF       ON        1
  ON        OFF       2
  ON        ON        3

Answer: 4 values (0 to 3) = 2²
```

**With THREE light bulbs:**
```
Bulb 1    Bulb 2    Bulb 3    Value
───────   ───────   ───────   ─────
  OFF       OFF       OFF       0
  OFF       OFF       ON        1
  OFF       ON        OFF       2
  OFF       ON        ON        3
  ON        OFF       OFF       4
  ON        OFF       ON        5
  ON        ON        OFF       6
  ON        ON        ON        7

Answer: 8 values (0 to 7) = 2³
```

**The Pattern:**
```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE POWER OF 2 FORMULA                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│    Number of possibilities = 2^(number of bits)                         │
│                                                                          │
│    1 bit  =  2¹ =     2 values  (0-1)                                   │
│    2 bits =  2² =     4 values  (0-3)                                   │
│    3 bits =  2³ =     8 values  (0-7)                                   │
│    4 bits =  2⁴ =    16 values  (0-15)                                  │
│    8 bits =  2⁸ =   256 values  (0-255)   ← THIS IS A BYTE!            │
│   32 bits = 2³² = 4.3 billion values      ← THIS IS AN IPv4 ADDRESS!   │
│                                                                          │
│    Why 2? Because each switch has exactly 2 states: ON or OFF           │
└─────────────────────────────────────────────────────────────────────────┘
```

### 2.3 The Birth of the Byte

**The Year:** 1960s-1970s  
**The Decision:** How many switches should we group together?

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CHOOSING THE BYTE SIZE                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   4 bits (nibble):   0-15      ❌ Too small! Can't even store alphabet  │
│   8 bits (byte):     0-255     ✅ Perfect! Letters, numbers, symbols    │
│   16 bits:           0-65,535  ❌ Wasteful, hardware was expensive      │
│                                                                          │
│   The Winner: 8 BITS = 1 BYTE (also called "OCTET" in networking)       │
│                                                                          │
│   Why 255 is the maximum for one byte:                                  │
│                                                                          │
│   Position:  128   64   32   16    8    4    2    1                      │
│   All ON:     1    1    1    1    1    1    1    1                       │
│   Sum:      128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255                    │
│                                                                          │
│   Plus zero (all OFF) = 256 total values (0 to 255)                     │
└─────────────────────────────────────────────────────────────────────────┘
```

**Binary Position Values (MEMORIZE THIS!):**

| Position | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 |
|----------|---|---|---|---|---|---|---|---|
| **Value** | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

**Example Conversions:**

| Decimal | Binary | Calculation |
|---------|--------|-------------|
| 192 | 11000000 | 128 + 64 = 192 |
| 168 | 10101000 | 128 + 32 + 8 = 168 |
| 255 | 11111111 | 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255 |
| 0 | 00000000 | All switches OFF |

### 2.4 From Bits to IP Addresses

**The Year:** 1981 (RFC 791)  
**The Decision:** How long should an internet address be?

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE BIRTH OF IPv4                                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Question: "How long should an internet address be?"                   │
│                                                                          │
│   Decision: Use 4 BYTES (32 bits total)                                 │
│                                                                          │
│   Why 4 bytes?                                                          │
│   ✅ Easy for humans to read: 192.168.1.10                              │
│   ✅ Each byte (0-255) fits in human brain easily                       │
│   ✅ 2³² = 4.3 billion addresses seemed infinite in 1981                │
│      (They were wrong... hence IPv6 today!)                             │
│                                                                          │
│                        AN IPv4 ADDRESS                                   │
│   ┌───────────┬───────────┬───────────┬───────────┐                     │
│   │    192    │    168    │     1     │    10     │                     │
│   ├───────────┼───────────┼───────────┼───────────┤                     │
│   │  8 bits   │  8 bits   │  8 bits   │  8 bits   │                     │
│   │  (octet)  │  (octet)  │  (octet)  │  (octet)  │                     │
│   └───────────┴───────────┴───────────┴───────────┘                     │
│        └────────────────────┬────────────────────┘                      │
│                      32 bits total                                      │
│                                                                          │
│   In Binary:                                                            │
│   11000000.10101000.00000001.00001010                                   │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# Part III: IP Addressing — The City Metaphor

## 3. The 10-Floor Tower of Networking

Think of networking as a **10-floor building**. Each floor builds on the one below:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE NETWORKING TOWER                                  │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   🏢 FLOOR 10: Full Internet                                            │
│   │           └── Millions of connected neighborhoods                    │
│   │                                                                      │
│   🏢 FLOOR 9:  Subnetting                                               │
│   │           └── Dividing neighborhoods into smaller blocks            │
│   │                                                                      │
│   🏢 FLOOR 8:  Special Addresses                                        │
│   │           └── Reserved numbers (0, 255, loopback 127.0.0.1)         │
│   │                                                                      │
│   🏢 FLOOR 7:  Broadcasts                                               │
│   │           └── Shouting to everyone in the neighborhood              │
│   │                                                                      │
│   🏢 FLOOR 6:  Multiple Routers                                         │
│   │           └── Courier system across districts                        │
│   │                                                                      │
│   🏢 FLOOR 5:  Routing Tables                                           │
│   │           └── GPS maps stored in routers                            │
│   │                                                                      │
│   🏢 FLOOR 4:  Local vs Remote                                          │
│   │           └── Is the destination in my neighborhood or far away?    │
│   │                                                                      │
│   🏢 FLOOR 3:  Gateway/Router                                           │
│   │           └── The post office that redirects mail to other areas    │
│   │                                                                      │
│   🏢 FLOOR 2:  Subnet Mask                                              │
│   │           └── The fence that marks your neighborhood boundary       │
│   │                                                                      │
│   🏢 FLOOR 1:  IP Address                                               │
│   │           └── Your house number in the digital city                 │
│   │                                                                      │
│   🏗️ FOUNDATION: Binary (32 bits = 4 bytes)                             │
│               └── The construction material everything is built from    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

## 4. IP Addresses: Your Digital House Number

### 4.1 What Is an IP Address?

**IP** = **I**nternet **P**rotocol

An IP address is a **unique identifier** for a device on a network — like a house number in a city.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    IP ADDRESS = HOUSE ADDRESS                            │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Real World:                    Digital World:                         │
│   ───────────                    ──────────────                         │
│   123 Main Street                192.168.1.10                           │
│   Springfield, IL 62701          │   │   │  │                           │
│   USA                            │   │   │  └── House number (host)     │
│                                  │   │   └───── Block number            │
│                                  │   └───────── Street (network)        │
│                                  └───────────── City/Region             │
│                                                                          │
│   Just like no two houses can have the same address,                    │
│   no two devices can have the same IP address on the same network!      │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4.2 Network vs Host: Street vs House

Every IP address has TWO parts:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NETWORK vs HOST PORTION                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│                      192.168.1.14                                        │
│                      ─────── ──                                          │
│                         │    │                                           │
│                         │    └── HOST portion (identifies the device)   │
│                         │        "Which HOUSE on the street?"            │
│                         │                                                │
│                         └─────── NETWORK portion (identifies the network)│
│                                  "Which STREET in the city?"             │
│                                                                          │
│   The SUBNET MASK tells you where to split!                             │
│                                                                          │
│   With /24 (255.255.255.0):                                             │
│   ┌─────────────────────────┬───────────┐                               │
│   │   192  .  168  .  1     │    14     │                               │
│   │      NETWORK            │   HOST    │                               │
│   │   (Which neighborhood?) │ (Which    │                               │
│   │                         │  house?)  │                               │
│   └─────────────────────────┴───────────┘                               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4.3 Reserved & Special Addresses

**These addresses have special purposes and CANNOT be assigned to regular devices:**

| Address Type | Example | Purpose | Can Assign? |
|--------------|---------|---------|-------------|
| **Network Address** | 192.168.1.0 | Identifies the network itself | ❌ NO |
| **Broadcast Address** | 192.168.1.255 | Send to ALL devices in network | ❌ NO |
| **Loopback** | 127.0.0.1 | "Talk to myself" (localhost) | ❌ NO |
| **APIPA** | 169.254.x.x | Auto-assigned when DHCP fails | ⚠️ Automatic |
| **All Zeros** | 0.0.0.0 | "Any address" / Default route | Special |
| **All Ones** | 255.255.255.255 | Limited broadcast | Special |

```
┌─────────────────────────────────────────────────────────────────────────┐
│              UNDERSTANDING NETWORK & BROADCAST ADDRESSES                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Network: 192.168.1.0/24                                               │
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                                                                  │   │
│   │   192.168.1.0   ← NETWORK ADDRESS (First address)               │   │
│   │   ────────────     "This is the neighborhood's identity"        │   │
│   │       │            Cannot be assigned to any device!            │   │
│   │       │                                                          │   │
│   │   192.168.1.1   ← FIRST USABLE ADDRESS                          │   │
│   │   192.168.1.2      (Often assigned to the router/gateway)       │   │
│   │   192.168.1.3                                                    │   │
│   │      ...                                                         │   │
│   │   192.168.1.253                                                  │   │
│   │   192.168.1.254 ← LAST USABLE ADDRESS                           │   │
│   │       │                                                          │   │
│   │       │                                                          │   │
│   │   192.168.1.255 ← BROADCAST ADDRESS (Last address)              │   │
│   │   ─────────────    "Shout to EVERYONE in this neighborhood"     │   │
│   │                    Cannot be assigned to any device!            │   │
│   │                                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   Total Addresses: 256 (0 to 255)                                       │
│   Usable Addresses: 254 (Total - Network - Broadcast = 256 - 2)         │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 4.4 Private vs Public IP Ranges

**Not all IP addresses are visible on the internet!**

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    PRIVATE IP RANGES (RFC 1918)                          │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   These ranges are reserved for INTERNAL networks only:                 │
│   They CANNOT be routed on the public internet!                         │
│                                                                          │
│   ┌──────────────────────┬───────────┬──────────────────────────────┐   │
│   │ Range                │ CIDR      │ Usable Addresses              │   │
│   ├──────────────────────┼───────────┼──────────────────────────────┤   │
│   │ 10.0.0.0 -           │ /8        │ 16,777,214                   │   │
│   │ 10.255.255.255       │           │ (Large organizations)        │   │
│   ├──────────────────────┼───────────┼──────────────────────────────┤   │
│   │ 172.16.0.0 -         │ /12       │ 1,048,574                    │   │
│   │ 172.31.255.255       │           │ (Medium organizations)       │   │
│   ├──────────────────────┼───────────┼──────────────────────────────┤   │
│   │ 192.168.0.0 -        │ /16       │ 65,534                       │   │
│   │ 192.168.255.255      │           │ (Home/Small office) ← COMMON │   │
│   └──────────────────────┴───────────┴──────────────────────────────┘   │
│                                                                          │
│   Why Private IPs Exist:                                                │
│   • IPv4 only has 4.3 billion addresses (not enough for everyone!)     │
│   • Private IPs can be reused in different networks                    │
│   • NAT translates private → public when accessing internet            │
│                                                                          │
│   Your home router:                                                     │
│   ┌─────────────┐                                                       │
│   │  Internet   │  Public IP: 73.142.56.89 (unique worldwide)          │
│   │   (WAN)     │                                                       │
│   └──────┬──────┘                                                       │
│          │ [ROUTER + NAT]                                               │
│   ┌──────┴──────┐                                                       │
│   │    Home     │  Private IPs: 192.168.1.x (reused in millions        │
│   │   (LAN)     │               of homes worldwide!)                   │
│   └─────────────┘                                                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# Part IV: Subnet Masks — The Neighborhood Fence

## 5. Subnet Masks Explained

### 5.1 What Is a Subnet Mask?

A **subnet mask** is the **fence** that defines the boundary of your network neighborhood.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SUBNET MASK = NEIGHBORHOOD FENCE                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Imagine a city where every house has an address:                      │
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                        THE CITY                                  │   │
│   │                                                                  │   │
│   │   ┌─────────────────┐     ┌─────────────────┐                   │   │
│   │   │  Neighborhood A │     │  Neighborhood B │                   │   │
│   │   │  192.168.1.x    │     │  192.168.2.x    │                   │   │
│   │   │   ┌───┐ ┌───┐   │     │   ┌───┐ ┌───┐   │                   │   │
│   │   │   │.1 │ │.2 │   │     │   │.1 │ │.2 │   │                   │   │
│   │   │   └───┘ └───┘   │     │   └───┘ └───┘   │                   │   │
│   │   │   ┌───┐ ┌───┐   │     │   ┌───┐ ┌───┐   │                   │   │
│   │   │   │.3 │ │.4 │   │     │   │.3 │ │.4 │   │                   │   │
│   │   │   └───┘ └───┘   │     │   └───┘ └───┘   │                   │   │
│   │   │ ════════════════│=====│════════════════ │                   │   │
│   │   │   THE FENCE     │     │   THE FENCE     │                   │   │
│   │   │ (Subnet Mask)   │     │ (Subnet Mask)   │                   │   │
│   │   └─────────────────┘     └─────────────────┘                   │   │
│   │                                                                  │   │
│   │   The FENCE (subnet mask) tells you:                            │   │
│   │   • Which houses are in YOUR neighborhood (direct communication) │   │
│   │   • Which houses are OUTSIDE (need a router/post office)        │   │
│   │                                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   Subnet Mask: 255.255.255.0 means:                                     │
│   "The first three numbers define the neighborhood,                     │
│    the last number identifies houses within it."                        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Key Insight:** The subnet mask has TWO parts:
- **1s (255)** = Network portion (LOCKED, defines the neighborhood)
- **0s (0)** = Host portion (FLEXIBLE, house numbers)

```
┌─────────────────────────────────────────────────────────────────────────┐
│              SUBNET MASK IN BINARY                                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   255.255.255.0 in binary:                                              │
│                                                                          │
│   11111111.11111111.11111111.00000000                                   │
│   ├────────────────────────┤├───────┤                                   │
│   │      ALL 1s = 24 bits  ││  0s   │                                   │
│   │      (Network portion) ││(Host) │                                   │
│   └────────────────────────┘└───────┘                                   │
│                                                                          │
│   Rule: 1s = LOCKED (network)    0s = FREE (hosts)                      │
│   Rule: 1s are always CONTIGUOUS (no gaps!)                             │
│                                                                          │
│   ✅ Valid:   11111111.11111111.11111111.00000000  (255.255.255.0)      │
│   ✅ Valid:   11111111.11111111.11111111.11000000  (255.255.255.192)    │
│   ❌ INVALID: 11111111.11111111.11110000.11110000  (gaps in 1s!)        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5.2 The AND Operation: How Computers Calculate Networks

When a computer needs to know if another device is in the same network, it performs a **bitwise AND**:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE BINARY AND OPERATION                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   AND Truth Table:                                                      │
│   ┌─────┬─────┬────────┐                                                │
│   │  A  │  B  │ A AND B│                                                │
│   ├─────┼─────┼────────┤                                                │
│   │  0  │  0  │   0    │                                                │
│   │  0  │  1  │   0    │                                                │
│   │  1  │  0  │   0    │                                                │
│   │  1  │  1  │   1    │  ← Only 1 AND 1 = 1                            │
│   └─────┴─────┴────────┘                                                │
│                                                                          │
│   Example: What network is 192.168.1.50 in (with mask /24)?             │
│                                                                          │
│   IP Address:   192.168.1.50                                            │
│   Binary:       11000000.10101000.00000001.00110010                     │
│                                                                          │
│   Subnet Mask:  255.255.255.0                                           │
│   Binary:       11111111.11111111.11111111.00000000                     │
│                                                                          │
│   AND Operation:                                                        │
│   ─────────────────────────────────────────────                         │
│   11000000.10101000.00000001.00110010  (IP: 192.168.1.50)               │
│   11111111.11111111.11111111.00000000  (Mask: 255.255.255.0)            │
│   ─────────────────────────────────────────────                         │
│   11000000.10101000.00000001.00000000  (Network: 192.168.1.0) ✅        │
│                                                                          │
│   The AND operation "masks out" the host portion, revealing the network!│
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Determining if Two IPs Are on the Same Network:**

```
Question: Are 192.168.1.50 and 192.168.1.100 on the same /24 network?

Step 1: AND first IP with mask
        192.168.1.50 AND 255.255.255.0 = 192.168.1.0

Step 2: AND second IP with mask
        192.168.1.100 AND 255.255.255.0 = 192.168.1.0

Step 3: Compare results
        192.168.1.0 == 192.168.1.0 ✅ SAME NETWORK!

If same → Direct communication (no router needed)
If different → Need router to communicate
```

### 5.3 CIDR Notation: The Network Engineer's Shorthand

**CIDR** = **C**lassless **I**nter-**D**omain **R**outing

Instead of writing `255.255.255.0`, engineers write `/24`.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    CIDR: THE PRECISION KNIFE                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   CIDR notation tells you: "How many bits are locked for the network?"  │
│                                                                          │
│   192.168.1.0/24                                                        │
│              ├──                                                        │
│              │                                                          │
│              └── "Lock the first 24 bits for the network"               │
│                  "Leave the remaining 8 bits for hosts"                 │
│                                                                          │
│   Visual:                                                               │
│   ┌────────────────────────────────────────────────────┐                │
│   │ 11000000.10101000.00000001 │ 00000000             │                │
│   │ ←────── 24 bits LOCKED ───→│←── 8 bits FREE ────→ │                │
│   │        (Network)           │      (Hosts)         │                │
│   └────────────────────────────────────────────────────┘                │
│                                                                          │
│   Host bits = 32 - CIDR number                                          │
│   /24 → 32 - 24 = 8 host bits → 2⁸ = 256 addresses                     │
│   /25 → 32 - 25 = 7 host bits → 2⁷ = 128 addresses                     │
│   /26 → 32 - 26 = 6 host bits → 2⁶ = 64 addresses                      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 5.4 The Class System (Historical Context)

Before CIDR (1993), networks came in only **three fixed sizes**:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE OLD CLASS SYSTEM (1981-1993)                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Class A: Starts with 0-127                                            │
│   ┌─────────────┬─────────────────────────────────────────┐             │
│   │   Network   │              Host                        │             │
│   │   (8 bits)  │            (24 bits)                     │             │
│   └─────────────┴─────────────────────────────────────────┘             │
│   Mask: 255.0.0.0 (/8) → 16,777,214 hosts per network                   │
│   Problem: WAY too big! Apple got one, and they don't need 16 million!  │
│                                                                          │
│   Class B: Starts with 128-191                                          │
│   ┌───────────────────────┬───────────────────────────────┐             │
│   │       Network         │            Host                │             │
│   │       (16 bits)       │          (16 bits)             │             │
│   └───────────────────────┴───────────────────────────────┘             │
│   Mask: 255.255.0.0 (/16) → 65,534 hosts per network                    │
│                                                                          │
│   Class C: Starts with 192-223                                          │
│   ┌───────────────────────────────────────┬───────────────┐             │
│   │              Network                   │     Host      │             │
│   │             (24 bits)                  │   (8 bits)    │             │
│   └───────────────────────────────────────┴───────────────┘             │
│   Mask: 255.255.255.0 (/24) → 254 hosts per network                     │
│                                                                          │
│   THE PROBLEM (The "Store with Only 3 Bag Sizes"):                      │
│   • Company needs 1,000 addresses                                       │
│   • Class C too small (254), Class B too big (65,534)                  │
│   • Forced to buy Class B → WASTES 64,534 addresses!                   │
│                                                                          │
│   THE SOLUTION: CIDR (1993)                                             │
│   → Cut networks to ANY size you want (/28, /26, /22, anything!)       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# Part V: Subnetting Mathematics

## 6. The Three Calculation Methods

> **The Universal Formula:**
> ```
> Host bits = 32 - CIDR number
> Total addresses = 2^(host bits)
> Usable addresses = Total - 2 (network & broadcast)
> ```

### 6.1 Method 1: Magic Number (Fastest) ⚡

The **Magic Number** is the size of each network block.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE MAGIC NUMBER METHOD                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ★ FORMULA: Magic Number = 256 - (Last non-zero octet of subnet mask) │
│                                                                          │
│   Examples:                                                             │
│   ┌─────────────────────┬──────────────────┬─────────────────┐          │
│   │ Subnet Mask         │ Calculation      │ Magic Number    │          │
│   ├─────────────────────┼──────────────────┼─────────────────┤          │
│   │ 255.255.255.0       │ 256 - 0 = 256    │ 256             │          │
│   │ 255.255.255.128     │ 256 - 128 = 128  │ 128             │          │
│   │ 255.255.255.192     │ 256 - 192 = 64   │ 64              │          │
│   │ 255.255.255.224     │ 256 - 224 = 32   │ 32              │          │
│   │ 255.255.255.240     │ 256 - 240 = 16   │ 16              │          │
│   │ 255.255.255.248     │ 256 - 248 = 8    │ 8               │          │
│   │ 255.255.255.252     │ 256 - 252 = 4    │ 4               │          │
│   └─────────────────────┴──────────────────┴─────────────────┘          │
│                                                                          │
│   The magic number tells you:                                           │
│   • How many addresses in each network                                  │
│   • Where network boundaries fall (multiples of magic number)           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Step-by-Step Example:**

```
Given: IP = 192.168.1.50   Mask = 255.255.255.192 (/26)

STEP 1: Find Magic Number
        256 - 192 = 64

STEP 2: Find Network Start
        50 ÷ 64 = 0.78... → Take integer part: 0
        0 × 64 = 0
        Network starts at: 192.168.1.0

STEP 3: Find Network Range
        Start: 0
        End: 0 + 64 - 1 = 63
        Range: 192.168.1.0 to 192.168.1.63

STEP 4: Find Usable IPs
        First usable: 192.168.1.1 (Network + 1)
        Last usable: 192.168.1.62 (Broadcast - 1)
        Broadcast: 192.168.1.63

ANSWER:
┌────────────────────────────────────────┐
│ Network ID:    192.168.1.0/26          │
│ First Host:    192.168.1.1             │
│ Last Host:     192.168.1.62            │
│ Broadcast:     192.168.1.63            │
│ Usable IPs:    62                      │
└────────────────────────────────────────┘
```

### 6.2 Method 2: Block Size Calculation

Same concept, different terminology:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    BLOCK SIZE METHOD                                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Given: IP = X.X.X.Y   Mask = 255.255.255.M                            │
│                                                                          │
│   Step 1: Block Size                                                    │
│           Block = 256 - M                                               │
│                                                                          │
│   Step 2: Network Start                                                 │
│           Network = (Y ÷ Block) × Block                                 │
│           (Take integer part of division!)                              │
│                                                                          │
│   Step 3: Network Range                                                 │
│           Start: Network                                                │
│           End: Network + Block - 1                                      │
│                                                                          │
│   Step 4: Usable IPs                                                    │
│           Start + 1 to End - 1                                          │
│           (Skip first and last!)                                        │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Example:**

```
IP: 112.227.118.132    Mask: 255.255.255.128 (/25)

Step 1: Block Size
        256 - 128 = 128

Step 2: Network Start
        132 ÷ 128 = 1.03... → 1
        1 × 128 = 128
        Network: 112.227.118.128

Step 3: Range
        Start: 128
        End: 128 + 128 - 1 = 255
        Range: 112.227.118.128 to 112.227.118.255

Step 4: Usable
        112.227.118.129 to 112.227.118.254
        (129, 130, 131, 132, 133... up to 254)
```

### 6.3 Method 3: Binary AND (Most Accurate)

When in doubt, binary never lies:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    BINARY AND METHOD                                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Example: Is 112.227.118.132 on same network as 112.227.118.133?       │
│            Using mask 255.255.255.128                                    │
│                                                                          │
│   Step 1: Convert first IP to binary and AND with mask                  │
│                                                                          │
│   IP:   112.227.118.132                                                 │
│   Bin:  01110000.11100011.01110110.10000100                             │
│                                                                          │
│   Mask: 255.255.255.128                                                 │
│   Bin:  11111111.11111111.11111111.10000000                             │
│                                                                          │
│   AND:  01110000.11100011.01110110.10000000 = 112.227.118.128           │
│                                                                          │
│   Step 2: Convert second IP and AND with mask                           │
│                                                                          │
│   IP:   112.227.118.133                                                 │
│   Bin:  01110000.11100011.01110110.10000101                             │
│                                                                          │
│   AND:  01110000.11100011.01110110.10000000 = 112.227.118.128           │
│                                                                          │
│   Step 3: Compare                                                       │
│   Result 1: 112.227.118.128                                             │
│   Result 2: 112.227.118.128                                             │
│                                                                          │
│   ✅ SAME NETWORK! They can communicate directly.                       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 7. Complete CIDR Reference Table

### Quick Reference: Common Subnets

| CIDR | Subnet Mask | Total IPs | Usable IPs | Use Case |
|------|-------------|-----------|------------|----------|
| /30 | 255.255.255.252 | 4 | 2 | Point-to-point links |
| /29 | 255.255.255.248 | 8 | 6 | Small office (5-6 devices) |
| /28 | 255.255.255.240 | 16 | 14 | Small department |
| /27 | 255.255.255.224 | 32 | 30 | Small building |
| /26 | 255.255.255.192 | 64 | 62 | Medium office |
| /25 | 255.255.255.128 | 128 | 126 | Large department |
| /24 | 255.255.255.0 | 256 | 254 | Standard subnet |
| /23 | 255.255.254.0 | 512 | 510 | 2 combined subnets |
| /22 | 255.255.252.0 | 1,024 | 1,022 | Small campus |
| /16 | 255.255.0.0 | 65,536 | 65,534 | Large organization |
| /8 | 255.0.0.0 | 16,777,216 | 16,777,214 | ISP allocation |

### Complete CIDR Table (/8 to /32)

<details>
<summary><strong>Click to expand full CIDR table</strong></summary>

| CIDR | Subnet Mask | Binary | Network Bits | Host Bits | Total Addresses |
|------|-------------|--------|--------------|-----------|-----------------|
| /32 | 255.255.255.255 | 11111111.11111111.11111111.11111111 | 32 | 0 | 1 |
| /31 | 255.255.255.254 | 11111111.11111111.11111111.11111110 | 31 | 1 | 2 |
| /30 | 255.255.255.252 | 11111111.11111111.11111111.11111100 | 30 | 2 | 4 |
| /29 | 255.255.255.248 | 11111111.11111111.11111111.11111000 | 29 | 3 | 8 |
| /28 | 255.255.255.240 | 11111111.11111111.11111111.11110000 | 28 | 4 | 16 |
| /27 | 255.255.255.224 | 11111111.11111111.11111111.11100000 | 27 | 5 | 32 |
| /26 | 255.255.255.192 | 11111111.11111111.11111111.11000000 | 26 | 6 | 64 |
| /25 | 255.255.255.128 | 11111111.11111111.11111111.10000000 | 25 | 7 | 128 |
| /24 | 255.255.255.0 | 11111111.11111111.11111111.00000000 | 24 | 8 | 256 |
| /23 | 255.255.254.0 | 11111111.11111111.11111110.00000000 | 23 | 9 | 512 |
| /22 | 255.255.252.0 | 11111111.11111111.11111100.00000000 | 22 | 10 | 1,024 |
| /21 | 255.255.248.0 | 11111111.11111111.11111000.00000000 | 21 | 11 | 2,048 |
| /20 | 255.255.240.0 | 11111111.11111111.11110000.00000000 | 20 | 12 | 4,096 |
| /19 | 255.255.224.0 | 11111111.11111111.11100000.00000000 | 19 | 13 | 8,192 |
| /18 | 255.255.192.0 | 11111111.11111111.11000000.00000000 | 18 | 14 | 16,384 |
| /17 | 255.255.128.0 | 11111111.11111111.10000000.00000000 | 17 | 15 | 32,768 |
| /16 | 255.255.0.0 | 11111111.11111111.00000000.00000000 | 16 | 16 | 65,536 |
| /15 | 255.254.0.0 | 11111111.11111110.00000000.00000000 | 15 | 17 | 131,072 |
| /14 | 255.252.0.0 | 11111111.11111100.00000000.00000000 | 14 | 18 | 262,144 |
| /13 | 255.248.0.0 | 11111111.11111000.00000000.00000000 | 13 | 19 | 524,288 |
| /12 | 255.240.0.0 | 11111111.11110000.00000000.00000000 | 12 | 20 | 1,048,576 |
| /11 | 255.224.0.0 | 11111111.11100000.00000000.00000000 | 11 | 21 | 2,097,152 |
| /10 | 255.192.0.0 | 11111111.11000000.00000000.00000000 | 10 | 22 | 4,194,304 |
| /9 | 255.128.0.0 | 11111111.10000000.00000000.00000000 | 9 | 23 | 8,388,608 |
| /8 | 255.0.0.0 | 11111111.00000000.00000000.00000000 | 8 | 24 | 16,777,216 |

</details>

### Magic Number Quick Reference

| CIDR | Mask Last Octet | Magic Number | Networks per /24 |
|------|-----------------|--------------|------------------|
| /24 | 0 | 256 | 1 |
| /25 | 128 | 128 | 2 |
| /26 | 192 | 64 | 4 |
| /27 | 224 | 32 | 8 |
| /28 | 240 | 16 | 16 |
| /29 | 248 | 8 | 32 |
| /30 | 252 | 4 | 64 |
| /31 | 254 | 2 | 128 |
| /32 | 255 | 1 | 256 |

---

# Part VI: Network Devices

## 8. Hub, Switch, Router: The Evolution

### 8.1 Hub: The Dead Megaphone ☠️

**Status:** EXTINCT (obsolete since the 1990s)

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE HUB: A DUMB REPEATER                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   How a Hub Works:                                                      │
│                                                                          │
│                         ┌─────┐                                         │
│                         │ HUB │                                         │
│                      ┌──┴─────┴──┐                                      │
│                     /    │       \                                      │
│                   PC1   PC2     PC3                                     │
│                                                                          │
│   PC1 sends "Hello PC2!":                                               │
│   Hub: "I'M DUMB! I'll shout this to EVERYONE!"                        │
│                                                                          │
│        PC1 ──📢──→ HUB ──📢──→ PC2 (That's for me! ✅)                 │
│                     │                                                    │
│                     └──📢──→ PC3 (Not for me... ❌ ignores)             │
│                                                                          │
│   ┌──────────────────────────────────────────────────────────────┐      │
│   │ HUB CONSTRAINTS (What it CAN'T do):                          │      │
│   ├──────────────────────────────────────────────────────────────┤      │
│   │ ❌ Can't learn addresses                                      │      │
│   │ ❌ Can't prevent collisions                                   │      │
│   │ ❌ Can't provide privacy (everyone hears everything)          │      │
│   │ ❌ Can't connect different networks                           │      │
│   │ ✅ ONLY thing it does: Repeat signals to ALL ports           │      │
│   └──────────────────────────────────────────────────────────────┘      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 8.2 Switch: The Smart Mailman 📬

**Purpose:** Connect devices in the **SAME network** intelligently.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE SWITCH: LEARNS AND DELIVERS                       │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   How a Switch Works:                                                   │
│                                                                          │
│                        ┌────────┐                                       │
│                        │ SWITCH │                                       │
│                     ┌──┴────────┴──┐                                    │
│                    /     │         \                                    │
│                  PC1    PC2       PC3                                   │
│                Port 1  Port 2   Port 3                                  │
│                                                                          │
│   The Switch's Brain (MAC Address Table):                               │
│   ┌────────────┬─────────────────────────┐                              │
│   │   Port     │    MAC Address          │                              │
│   ├────────────┼─────────────────────────┤                              │
│   │   Port 1   │  AA:BB:CC:DD:EE:01     │ ← PC1                        │
│   │   Port 2   │  11:22:33:44:55:66     │ ← PC2                        │
│   │   Port 3   │  FF:EE:DD:CC:BB:AA     │ ← PC3                        │
│   └────────────┴─────────────────────────┘                              │
│                                                                          │
│   PC1 sends "Hello PC2!":                                               │
│   Switch: "I KNOW where PC2 is! Port 2. Delivering directly."          │
│                                                                          │
│        PC1 ──📧──→ SWITCH ──📧──→ PC2 only (Direct delivery! ✅)       │
│                              ❌ PC3 never sees it (Privacy!)            │
│                                                                          │
│   ┌──────────────────────────────────────────────────────────────┐      │
│   │ SWITCH CAPABILITIES & CONSTRAINTS:                           │      │
│   ├──────────────────────────────────────────────────────────────┤      │
│   │ ✅ Learns MAC addresses (builds table automatically)         │      │
│   │ ✅ Prevents collisions (separate collision domains)          │      │
│   │ ✅ Provides privacy (unicast to destination only)            │      │
│   │ ❌ CAN'T connect different networks!                         │      │
│   │ ❌ Only works within ONE IP range                            │      │
│   └──────────────────────────────────────────────────────────────┘      │
│                                                                          │
│   Use: Connect devices in SAME network (same IP range)                  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 8.3 Router: The Border Checkpoint 🚧

**Purpose:** Connect **DIFFERENT networks** together.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE ROUTER: THE BORDER CHECKPOINT                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   A router is like a person with DUAL CITIZENSHIP:                      │
│   It has one foot in Network A, one foot in Network B.                  │
│                                                                          │
│        ┌─────────────────┐                   ┌─────────────────┐        │
│        │   Network A     │                   │   Network B     │        │
│        │  192.168.1.0/24 │                   │  192.168.2.0/24 │        │
│        │                 │                   │                 │        │
│        │   ┌───┐ ┌───┐   │   ┌──────────┐   │   ┌───┐ ┌───┐   │        │
│        │   │.10│ │.20│   │   │  ROUTER  │   │   │.10│ │.20│   │        │
│        │   └─┬─┘ └─┬─┘   │   │          │   │   └─┬─┘ └─┬─┘   │        │
│        │     └──┬──┘     │   │ eth0 eth1│   │     └──┬──┘     │        │
│        │        │        │   │ .1   .1  │   │        │        │        │
│        │    [SWITCH]─────┼───┤          ├───┼────[SWITCH]     │        │
│        │                 │   └──────────┘   │                 │        │
│        └─────────────────┘                   └─────────────────┘        │
│                                                                          │
│   Router's Dual Citizenship:                                            │
│   • Interface eth0: 192.168.1.1 (Citizen of Network A)                 │
│   • Interface eth1: 192.168.2.1 (Citizen of Network B)                 │
│                                                                          │
│   When 192.168.1.10 wants to talk to 192.168.2.20:                      │
│   1. PC checks: "Is .2.20 in my network?" → NO (different network!)    │
│   2. PC sends to gateway (router): 192.168.1.1                         │
│   3. Router receives, checks routing table                              │
│   4. Router forwards out eth1 to Network B                              │
│   5. Switch in Network B delivers to 192.168.2.20                       │
│                                                                          │
│   ┌──────────────────────────────────────────────────────────────┐      │
│   │ ROUTER CAPABILITIES & CONSTRAINTS:                           │      │
│   ├──────────────────────────────────────────────────────────────┤      │
│   │ ✅ Connects DIFFERENT networks                               │      │
│   │ ✅ Routes between IP ranges                                  │      │
│   │ ✅ Has multiple interfaces (dual/multi citizenship)          │      │
│   │ ✅ Makes routing decisions based on routing table            │      │
│   │ ❌ More expensive than switches                              │      │
│   │ ❌ Slower than switches (more processing per packet)         │      │
│   └──────────────────────────────────────────────────────────────┘      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Summary Comparison

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NETWORK DEVICE COMPARISON                             │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   ┌──────────┬───────────────┬───────────────┬───────────────┐          │
│   │ Feature  │     HUB       │    SWITCH     │    ROUTER     │          │
│   ├──────────┼───────────────┼───────────────┼───────────────┤          │
│   │ Layer    │ Physical (1)  │ Data Link (2) │ Network (3)   │          │
│   │ Speed    │ Slow          │ Fast          │ Medium        │          │
│   │ Smart    │ ❌ Dumb       │ ✅ Learns     │ ✅ Routes     │          │
│   │ Privacy  │ ❌ None       │ ✅ Yes        │ ✅ Yes        │          │
│   │ Networks │ Same only     │ Same only     │ Different     │          │
│   │ Status   │ ☠️ DEAD       │ ✅ Common     │ ✅ Essential  │          │
│   └──────────┴───────────────┴───────────────┴───────────────┘          │
│                                                                          │
│   Mental Model:                                                         │
│   • Hub = Dumb megaphone (shouts to everyone)                           │
│   • Switch = Smart mailman (delivers to exact address)                  │
│   • Router = Border checkpoint (connects different countries)           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# Part VII: Routing

## 9. Routing Tables: The GPS of Networks

### 9.1 Understanding Routing Tables

A **routing table** is a set of rules that tells the router: *"To reach destination X, send packets through interface Y."*

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    ROUTING TABLE STRUCTURE                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Every routing entry has TWO parts:                                    │
│                                                                          │
│   1. DESTINATION (Left side): "Which network am I trying to reach?"     │
│      • Can be specific: 192.168.2.0/24                                  │
│      • Can be default: 0.0.0.0/0 (matches everything)                   │
│                                                                          │
│   2. GATEWAY/NEXT HOP (Right side): "Where do I send the packet?"       │
│      • Must be an IP address                                            │
│      • Must be REACHABLE (in my local network!)                         │
│                                                                          │
│   Example Routing Table:                                                │
│   ┌──────────────────────────┬────────────────────────┬─────────────┐   │
│   │      Destination         │    Gateway/Next Hop    │  Interface  │   │
│   ├──────────────────────────┼────────────────────────┼─────────────┤   │
│   │ 192.168.1.0/24           │ Directly connected     │ eth0        │   │
│   │ 192.168.2.0/24           │ 192.168.1.254          │ eth0        │   │
│   │ 10.0.0.0/8               │ 192.168.1.254          │ eth0        │   │
│   │ 0.0.0.0/0 (default)      │ 192.168.1.1            │ eth0        │   │
│   └──────────────────────────┴────────────────────────┴─────────────┘   │
│                                                                          │
│   Reading the table:                                                    │
│   • To reach 192.168.1.x → I'm directly connected, send directly       │
│   • To reach 192.168.2.x → Send to gateway 192.168.1.254               │
│   • To reach anywhere else → Send to default gateway 192.168.1.1       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 9.2 Default Routes

The **default route** is your fallback plan when you don't have a specific route.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    DEFAULT ROUTES EXPLAINED                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Default = "When lost, go HERE"                                        │
│                                                                          │
│   In NetPractice, you'll see:                                           │
│   ┌──────────────────┬─────────────────┐                                │
│   │   Destination    │     Gateway     │                                │
│   ├──────────────────┼─────────────────┤                                │
│   │    default       │  192.168.0.254  │                                │
│   │  (or 0.0.0.0/0)  │                 │                                │
│   └──────────────────┴─────────────────┘                                │
│                                                                          │
│   Computer's Decision Logic:                                            │
│                                                                          │
│   if (destination in my network):                                       │
│       send directly via switch                                          │
│   else if (specific route exists):                                      │
│       use that specific route                                           │
│   else:                                                                 │
│       use DEFAULT route ← "When all else fails!"                        │
│                                                                          │
│   ⚠️ CRITICAL RULE:                                                     │
│   The gateway IP MUST be reachable from your network!                   │
│                                                                          │
│   ✅ CORRECT:                                                           │
│   My IP: 192.168.1.10/24                                                │
│   Gateway: 192.168.1.254 (same network - reachable!)                    │
│                                                                          │
│   ❌ WRONG:                                                             │
│   My IP: 192.168.1.10/24                                                │
│   Gateway: 192.168.2.1 (different network - unreachable!)               │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 9.3 Local vs Remote Delivery

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    LOCAL vs REMOTE DELIVERY                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   When a computer wants to send data, it asks:                          │
│   "Is the destination in MY network?"                                   │
│                                                                          │
│   ┌───────────────────────────────────────────────────────────────┐     │
│   │                                                                │     │
│   │   My IP: 192.168.1.10/24                                      │     │
│   │   My Network: 192.168.1.0 - 192.168.1.255                     │     │
│   │                                                                │     │
│   │   Destination: 192.168.1.50                                   │     │
│   │   ┌────────────────────────────────────────────────────────┐  │     │
│   │   │ Is 192.168.1.50 in range 192.168.1.0-255?              │  │     │
│   │   │                                                        │  │     │
│   │   │ Answer: YES! ✅                                        │  │     │
│   │   │ Action: Send DIRECTLY via switch (no router needed)    │  │     │
│   │   └────────────────────────────────────────────────────────┘  │     │
│   │                                                                │     │
│   │   Destination: 192.168.2.50                                   │     │
│   │   ┌────────────────────────────────────────────────────────┐  │     │
│   │   │ Is 192.168.2.50 in range 192.168.1.0-255?              │  │     │
│   │   │                                                        │  │     │
│   │   │ Answer: NO! ❌                                         │  │     │
│   │   │ Action: Send to GATEWAY (router will forward)          │  │     │
│   │   └────────────────────────────────────────────────────────┘  │     │
│   │                                                                │     │
│   └───────────────────────────────────────────────────────────────┘     │
│                                                                          │
│   The subnet mask determines what's "local":                            │
│   IP AND Mask → Network                                                 │
│   If (my network == destination network) → LOCAL                        │
│   Else → REMOTE (needs router)                                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# Part VIII: NAT & DHCP

## 10. NAT: One Public IP, Many Devices

**NAT** = **N**etwork **A**ddress **T**ranslation

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    NAT: THE APARTMENT BUILDING ANALOGY                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   The Problem:                                                          │
│   • You have ONE public IP: 73.142.56.89                                │
│   • You have 10 devices wanting to use the internet                     │
│   • How does the router know which response goes to which device?       │
│                                                                          │
│   The Solution: PORT NUMBERS!                                           │
│                                                                          │
│   Think of it like an apartment building:                               │
│   • Building address (public IP): 73 Main Street                        │
│   • Apartment numbers (ports): 101, 102, 103...                         │
│                                                                          │
│        ┌─────────────────────────────────────────────────┐              │
│        │                  INTERNET                        │              │
│        │             sees: 73.142.56.89                   │              │
│        └────────────────────┬────────────────────────────┘              │
│                             │                                           │
│                      ┌──────┴──────┐                                    │
│                      │   ROUTER    │                                    │
│                      │   (NAT)     │                                    │
│                      │             │                                    │
│                      │ Public IP:  │                                    │
│                      │73.142.56.89 │                                    │
│                      └──────┬──────┘                                    │
│                             │                                           │
│        ┌────────────────────┼────────────────────┐                      │
│        │                    │                    │                      │
│   ┌────┴────┐         ┌────┴────┐         ┌────┴────┐                  │
│   │ Laptop  │         │  Phone  │         │   TV    │                  │
│   │.168.1.10│         │.168.1.11│         │.168.1.12│                  │
│   │Port:491 │         │Port:492 │         │Port:493 │                  │
│   └─────────┘         └─────────┘         └─────────┘                  │
│                                                                          │
│   NAT Translation Table:                                                │
│   ┌─────────────────────────┬─────────────────────────────────────┐     │
│   │ Internal                │ External (What internet sees)      │     │
│   ├─────────────────────────┼─────────────────────────────────────┤     │
│   │ 192.168.1.10:49152      │ 73.142.56.89:49152                  │     │
│   │ 192.168.1.11:49153      │ 73.142.56.89:49153                  │     │
│   │ 192.168.1.12:49154      │ 73.142.56.89:49154                  │     │
│   └─────────────────────────┴─────────────────────────────────────┘     │
│                                                                          │
│   The internet sees the same public IP, but different ports!            │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Port Number Ranges:**

| Range | Name | Use |
|-------|------|-----|
| 0-1023 | Well-Known | HTTP (80), HTTPS (443), DNS (53), SSH (22) |
| 1024-49151 | Registered | Application-specific |
| 49152-65535 | Dynamic/Private | NAT, temporary connections |

## 11. DHCP: The Hotel Check-In System

**DHCP** = **D**ynamic **H**ost **C**onfiguration **P**rotocol

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    DHCP: AUTOMATIC IP ASSIGNMENT                         │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Think of DHCP like a hotel front desk:                                │
│                                                                          │
│   ┌─────────────────────────────────────────────────────────────────┐   │
│   │                     HOTEL (NETWORK)                              │   │
│   │                                                                  │   │
│   │   Guest arrives         Front Desk checks           Guest gets   │   │
│   │   (new device)          available rooms             room key     │   │
│   │        │                     │                          │        │   │
│   │        ▼                     ▼                          ▼        │   │
│   │   ┌─────────┐          ┌─────────┐              ┌─────────────┐  │   │
│   │   │ "I need │          │ Room 301│              │ "You're in  │  │   │
│   │   │ a room!"│ ──────── │ is free!│ ──────────── │ room 301"   │  │   │
│   │   │         │          │         │              │             │  │   │
│   │   │ DISCOVER│          │ OFFER   │              │ ACK         │  │   │
│   │   └─────────┘          └─────────┘              └─────────────┘  │   │
│   │                                                                  │   │
│   └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│   DHCP Conversation (DORA):                                             │
│   1. DISCOVER: "Hello? Anyone have an IP for me?"                       │
│   2. OFFER: "I have 192.168.1.100 available!"                           │
│   3. REQUEST: "I'll take 192.168.1.100 please"                          │
│   4. ACK: "Done! 192.168.1.100 is yours for 24 hours"                   │
│                                                                          │
│   DHCP Lease Table:                                                     │
│   ┌──────────────────┬───────────┬─────────────┬─────────────┐          │
│   │ IP               │ Status    │ Lease Start │ Lease End   │          │
│   ├──────────────────┼───────────┼─────────────┼─────────────┤          │
│   │ 192.168.1.100    │ LEASED    │ 14:30 Mon   │ 14:30 Tue   │          │
│   │ 192.168.1.101    │ AVAILABLE │ -           │ -           │          │
│   │ 192.168.1.102    │ LEASED    │ 09:15 Mon   │ 09:15 Tue   │          │
│   │ 192.168.1.103    │ RESERVED  │ (Static)    │ (Static)    │          │
│   └──────────────────┴───────────┴─────────────┴─────────────┘          │
│                                                                          │
│   Why DHCP Matters:                                                     │
│   • No manual IP configuration needed                                   │
│   • Prevents duplicate IP addresses                                     │
│   • Efficient use of IP pool                                            │
│   • Works for temporary connections (laptops, phones)                   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# Part IX: NetPractice Levels

## Level 1: The Family Network

**The Scenario:** Four family computers connected to a switch that can't talk to each other.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    LEVEL 1: THE FAMILY NETWORK                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   🚨 ERROR MESSAGES:                                                    │
│   • "Invalid IP address on A"                                           │
│   • "Destination does not match any interface"                          │
│   • "Invalid IP on interface D1"                                        │
│                                                                          │
│   NETWORK TOPOLOGY:                                                     │
│                                                                          │
│       [My PC]          [Brother]                                        │
│          │                 │                                            │
│          A1                B1                                           │
│          │                 │                                            │
│          └────────┬────────┘                                            │
│                   │                                                     │
│              [SWITCH]                                                   │
│                   │                                                     │
│          ┌────────┴────────┐                                            │
│          │                 │                                            │
│          C1                D1                                           │
│          │                 │                                            │
│       [Mac]           [Sister]                                          │
│                                                                          │
│   THE PROBLEM:                                                          │
│   Family computers in the same house (switch) have no valid addresses!  │
│   Like family members without room numbers - they can't find each other!│
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**THE SOLUTION:**

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    LEVEL 1 SOLUTION                                      │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   Step 1: Choose a Network                                              │
│   Pick a private range: 192.168.1.0/24                                  │
│   This gives us 254 usable addresses (1-254)                            │
│                                                                          │
│   Step 2: Assign Unique House Numbers                                   │
│                                                                          │
│   ┌────────────────────────────────────────────────────────────────┐    │
│   │ Interface │        IP Address        │    Subnet Mask          │    │
│   ├───────────┼──────────────────────────┼─────────────────────────┤    │
│   │    A1     │      192.168.1.10        │    255.255.255.0        │    │
│   │    B1     │      192.168.1.11        │    255.255.255.0        │    │
│   │    C1     │      192.168.1.12        │    255.255.255.0        │    │
│   │    D1     │      192.168.1.13        │    255.255.255.0        │    │
│   └───────────┴──────────────────────────┴─────────────────────────┘    │
│                                                                          │
│   WHY THIS WORKS:                                                       │
│   ✅ Same network portion: 192.168.1.x                                  │
│   ✅ Same subnet mask: /24 (255.255.255.0)                              │
│   ✅ Unique host numbers: 10, 11, 12, 13                                │
│   ✅ All on same switch: Direct communication                           │
│                                                                          │
│   WHAT WOULD BREAK IT:                                                  │
│   ❌ Duplicate IPs: Two devices can't share the same address           │
│   ❌ Different masks: Devices would calculate different network bounds │
│   ❌ Different networks: 192.168.1.x can't directly reach 192.168.2.x  │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

**Level 1 Verification:**

| Check | Pass? |
|-------|-------|
| All IPs in same network (192.168.1.0/24) | ✅ |
| All subnet masks identical (255.255.255.0) | ✅ |
| All host portions unique (10, 11, 12, 13) | ✅ |
| No reserved addresses used (0, 255) | ✅ |

---

## Level 2-10: Progressive Challenges

Each level adds complexity. Here's what to expect:

| Level | New Concept | Key Challenge |
|-------|-------------|---------------|
| 1 | Basic IP assignment | Same network, unique IPs |
| 2 | Two networks + router | Configuring router interfaces |
| 3 | Routing tables | Setting default gateway |
| 4 | Multiple subnets | Different network ranges |
| 5 | Subnet sizing | Choosing appropriate CIDR |
| 6 | Complex routing | Multiple routers |
| 7 | Internet connection | Public vs private IPs |
| 8 | Cascading routers | Multi-hop routing |
| 9 | Network planning | Designing from scratch |
| 10 | Everything combined | Complete network architecture |

---

# Part X: Quick Reference

## Cheat Sheets

### 🔢 Subnetting Quick Math

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    SUBNETTING CHEAT SHEET                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   FORMULA 1: Host Count                                                 │
│   ────────────────────────                                              │
│   Host bits = 32 - CIDR                                                 │
│   Total addresses = 2^(host bits)                                       │
│   Usable = Total - 2                                                    │
│                                                                          │
│   FORMULA 2: Magic Number                                               │
│   ─────────────────────────                                             │
│   Magic = 256 - (last octet of mask)                                    │
│   Network boundaries = multiples of magic number                        │
│                                                                          │
│   FORMULA 3: Network ID                                                 │
│   ──────────────────────                                                │
│   Network = floor(host_octet / magic) × magic                          │
│                                                                          │
│   FORMULA 4: Broadcast                                                  │
│   ─────────────────────                                                 │
│   Broadcast = Network + Magic - 1                                       │
│                                                                          │
│   FORMULA 5: Usable Range                                               │
│   ─────────────────────────                                             │
│   First usable = Network + 1                                            │
│   Last usable = Broadcast - 1                                           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### 📋 Common Masks to Memorize

```
/24  =  255.255.255.0    =  256 addresses  =  254 usable
/25  =  255.255.255.128  =  128 addresses  =  126 usable
/26  =  255.255.255.192  =   64 addresses  =   62 usable
/27  =  255.255.255.224  =   32 addresses  =   30 usable
/28  =  255.255.255.240  =   16 addresses  =   14 usable
/29  =  255.255.255.248  =    8 addresses  =    6 usable
/30  =  255.255.255.252  =    4 addresses  =    2 usable
```

### 🔌 Binary Position Values

```
Position:   8    7    6    5    4    3    2    1
Value:    128   64   32   16    8    4    2    1
```

### 🏠 Private IP Ranges

```
10.0.0.0     - 10.255.255.255    (/8)    16 million addresses
172.16.0.0   - 172.31.255.255    (/12)   1 million addresses
192.168.0.0  - 192.168.255.255   (/16)   65,534 addresses
```

## Common Mistakes

### ❌ DON'T Do These:

| Mistake | Why It's Wrong | Fix |
|---------|----------------|-----|
| Using network address (.0) for a host | Reserved for network ID | Use .1 through .254 |
| Using broadcast address (.255) for a host | Reserved for broadcasts | Use .1 through .254 |
| Different masks on same network | Devices calculate different boundaries | Match all masks |
| Gateway not in local network | Can't reach unreachable gateway | Gateway must be local |
| Duplicate IP addresses | Address collision | Each IP must be unique |
| Overlapping networks | Routing confusion | Plan non-overlapping ranges |

### ✅ DO These:

1. **Plan before configuring**: Sketch the network first
2. **Use consistent subnets**: All devices on same network = same mask
3. **Document your ranges**: Know what's used, what's available
4. **Verify gateway reachability**: Gateway must be in your subnet
5. **Check for typos**: One wrong digit breaks everything

---

## Resources & Further Reading

### 📚 Official Documentation
- [RFC 791 - Internet Protocol](https://www.rfc-editor.org/rfc/rfc791) - The original IPv4 specification
- [RFC 1918 - Private Address Space](https://www.rfc-editor.org/rfc/rfc1918) - Private IP ranges
- [RFC 4632 - CIDR](https://www.rfc-editor.org/rfc/rfc4632) - Classless Inter-Domain Routing
- [IANA IP Allocations](https://www.iana.org/assignments/ipv4-address-space/) - Global IP registry

### 🎥 Video Tutorials
- [Networking Fundamentals](https://www.youtube.com/watch?v=POPoAjWFkGg)
- [Subnetting Made Easy](https://www.youtube.com/watch?v=eHV1aOnu7oM)
- [IP Addressing Explained](https://www.youtube.com/watch?v=sMHzfigUxz4)
- [CIDR Notation Tutorial](https://www.youtube.com/watch?v=7_LPdttKXPc)

### 🔧 Practice Tools
- [Subnet Calculator](https://www.subnet-calculator.com/)
- [IP Address Lookup](https://whois.arin.net/)
- [IP Reputation Check](https://www.abuseipdb.com/)

### 📖 42 School Resources
- [NetPractice Guide by ricardoreves](https://github.com/ricardoreves/42-net-practice)
- [NetPractice Guide by lpaube](https://github.com/lpaube/NetPractice)
- [Packet Coders Subnetting Guide](https://www.packetcoders.io/a-beginners-guide-to-subnetting/)

---

<div align="center">

## 🎓 Key Takeaways

</div>

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    THE FIVE LAWS OF NETWORKING                           │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│   1. NO DUPLICATES                                                      │
│      Every IP address must be unique within its network                 │
│                                                                          │
│   2. SAME NETWORK = SAME MASK                                           │
│      Devices that need to talk directly must share subnet mask          │
│                                                                          │
│   3. GATEWAY MUST BE REACHABLE                                          │
│      Your default gateway must be in YOUR network                       │
│                                                                          │
│   4. ROUTERS CONNECT DIFFERENT NETWORKS                                 │
│      Switches connect same network, routers connect different ones      │
│                                                                          │
│   5. RESERVED ADDRESSES ARE SACRED                                      │
│      Network ID and broadcast address cannot be assigned to hosts       │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

<div align="center">

---

**Made with 💡 for 42 School Students**

*"I don't learn by memorizing facts — I learn by building worlds."*

[![Back to Top](https://img.shields.io/badge/Back%20to-Top-blue?style=flat)](#-netpractice-the-complete-ip-networking-guide)

</div>
