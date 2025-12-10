NetPractice does one thing:
👉 It teaches you how to make machines talk to each other using correct addresses and routes.


arpanet:
Advance research project agency network

IMP = Interface Message Processor
insted of letting researches send magnatic tapes to each other and communicate this way we can let them communicate together using IMP


ISP:
Internet service provider.

DSL:

RFC:
    Request for comment
        a place where engineers talk about how to internet should work and how it should operate and it should behave
Topics to study:
    - CIDR. (Classless Inter-Domain Routing)


Core Learning Skills:
Subnetting Mathematics
CIDR Notation (Classless Inter-Domain Routing)
Routing Logic
Network Troubleshooting
IP Address Planning
TCP/IP UDP/NCP


Hierarchy & Levels (The Building Map of Networking)

Think of this like a 10-floor tower:

Foundation: Bits & bytes (IP = 32-bit number in IPv4).

    Floor 1: IP address = House number.

    Floor 2: Subnet mask = Fence that marks neighborhood.

    Floor 3: Gateway/router = Post office that redirects mail.

    Floor 4: Local vs remote delivery.

    Floor 5: Routing tables = Maps stored in routers.

    Floor 6: Multiple routers = Courier system across districts.

    Floor 7: Broadcasts = Shouting across a neighborhood.

    Floor 8: Special addresses (0, 255, loopback, etc).

    Floor 9: Subnetting = Dividing neighborhoods into smaller ones.

    Floor 10: Full internet = Millions of connected neighborhoods.


The Constraint Walls (what networking CANNOT do)

A house (IP address) cannot be duplicated — two houses can’t share the same number.

A neighborhood cannot overlap randomly — subnet masks carve clean blocks, not messy scribbles.

A courier cannot cross into another neighborhood without a gate (router).

A post office (router) cannot guess — you must tell it which road leads to which neighborhood.

If you break these, the city collapses. Letters vanish. Courier unions strike.



Network vs Host:

192.168.1.14
196 is the network unique number class of network.
the last digit assigned to each host uniquely identifies the machine.


🧮 THE BINARY SURGERY: How CIDR Cuts Networks
The 32-Bit Address Dissection:
Every IP address is 32 bits (4 bytes × 8 bits each).

Example: 192.168.1.0/24

Binary: 11000000.10101000.00000001.00000000
        |-------- 24 bits --------||8 bits|
        |    Network Portion      ||Host  |
        |     (District)          ||Numbers|
The /24 means:

First 24 bits = FROZEN (defines the neighborhood)
Last 8 bits = FLEXIBLE (house numbers 0-255)
🔢 CIDR CHEAT SHEET: Common Network Sizes
CIDR	Subnet Mask	Usable IPs	Real-World Use
/30	255.255.255.252	2	Point-to-point links
/29	255.255.255.248	6	Small office
/28	255.255.255.240	14	Department
/27	255.255.255.224	30	Small building
/26	255.255.255.192	62	Medium office
/25	255.255.255.128	126	Large department
/24	255.255.255.0	254	Standard subnet
/16	255.255.0.0	65,534	Large organization
⚡ CIDR CALCULATION: The Mental Math Tricks
Quick Formula:
Host bits = 32 - CIDR number
Total addresses = 2^(host bits)
Usable addresses = Total - 2 (subtract network & broadcast)
Examples:
/24 → 32-24 = 8 host bits → 2^8 = 256 total → 254 usable
/28 → 32-28 = 4 host bits → 2^4 = 16 total → 14 usable
/30 → 32-30 = 2 host bits → 2^2 = 4 total → 2 usable
🕵️ LEVEL 1 CRIME SCENE INVESTIGATION
🚨 THE EVIDENCE:
Victim: Four family computers can't talk to each other Crime Scene: Two separate communication failures Clues from the logs:

"invalid IP address on A"
"destination does not match any interface"
"invalid IP on interface D1"
🔍 FORENSIC ANALYSIS:
The Problem:
Your family computers are in the same house (switch) but have no valid addresses!

It's like having four family members in the same house, but none of them have room numbers - they can't find each other!

The Network Topology:
[My PC] ---- \
              \
[Brother] ---- [SWITCH] ---- [Mac]
                            /
               [Sister] ----/
All devices are on ONE network - they should all be neighbors!

🛠️ THE SOLUTION BLUEPRINT:
Step 1: Choose a Network District
Pick a private network range (like choosing a neighborhood):

192.168.1.0/24 (gives you 254 addresses)
Step 2: Assign House Numbers
Give each device a unique address in the same neighborhood:

Interface A1 (My PC):           192.168.1.10/24
Interface B1 (Brother):        192.168.1.11/24  
Interface C1 (Mac):            192.168.1.12/24
Interface D1 (Sister):         192.168.1.13/24
Step 3: The Mathematical Verification
Network: 192.168.1.0/24

Network portion: 192.168.1 (first 24 bits locked)
Host portion: Last 8 bits (0-255)
Subnet mask: 255.255.255.0
All devices share:

Same network portion: ✅ 192.168.1.x
Same subnet mask: ✅ /24
Unique host numbers: ✅ 10, 11, 12, 13
⚙️ CONFIGURATION INPUT:
Fill in the NetPractice interface:

Interface A1:
IP: 192.168.1.10
Mask: 255.255.255.0

Interface B1:
IP: 192.168.1.11
Mask: 255.255.255.0

Interface C1:
IP: 192.168.1.12
Mask: 255.255.255.0

Interface D1:
IP: 192.168.1.13
Mask: 255.255.255.0
🧪 IMPOSSIBILITY TESTS:
What would BREAK this solution?

❌ Wrong: Giving two devices the same IP

Like two siblings claiming the same bedroom!
❌ Wrong: Using different subnet masks

Like family members using different addressing systems
❌ Wrong: Using addresses from different networks

Like putting family members in different neighborhoods
What makes it WORK?

✅ Correct: All devices in same network (192.168.1.x/24) ✅ Correct: Unique IP addresses for each device
✅ Correct: Same subnet mask (255.255.255.0)

🎯 CHALLENGE: Test Your Understanding
Question: Why can't we use these addresses?

A1: 192.168.1.10/24
B1: 192.168.2.11/24  ← Different network!
C1: 192.168.1.12/24
D1: 192.168.1.13/24
Answer: Device B is in a different postal district (192.168.2.x vs 192.168.1.x). They can't communicate directly - they'd need a router (post office) to forward messages between neighborhoods!

🚀 LEVEL UP: What's Next?
After Level 1, you'll encounter:

Routers (connecting different neighborhoods)
Routing tables (postal sorting rules)
Gateway configuration (finding the post office)
Complex topologies (multiple networks interconnected)
The Pattern: Each level adds one more layer of complexity, but the fundamentals remain the same - proper addressing and routing!

Which concept needs more drilling:

CIDR mathematics - More binary surgery practice
Subnetting scenarios - Different network size planning
Routing fundamentals - Preparing for multi-network levels
Troubleshooting methodology - Systematic network debugging



What is a subnet mask what is an ip address, what is the point of get my config, why would I Need it? like what actually are they? what do they stand for etc why are all ip addresses 192? or is this the defualt?

lets dive into this:

Subnetting Mathematics - The binary wizardry behind network division

CIDR Notation - The shorthand language of network engineers

Routing Logic - How packets find their way across the internet

AND WHERE DOES SWITCH AND ROUTERS PLAY A ROLE?


For broadcast IP we can say Networkid subnet - 1


IMP Transmission:

Computers speak electricity, phone lines speak sound. IMP is the translator: electricity → musical tones → electricity.

Computer Formats:

Can't have standards before inventing the thing. Each company invented computers independently, like different languages evolving in isolated tribes.

TCP/IP Evolution:

You can't invent the solution before experiencing the problem. NCP taught us what broke, TCP/IP fixed it.

Modern Devices:

Router = IMP's great-grandchild. Same job (translate between systems), different technology (faster, smarter, cheaper).

2.4GHz Interference:

Radio spectrum is a shared highway. If you broadcast on someone else's frequency, you cause traffic collisions. Legal = respect the lanes.


📜 THE ORIGIN STORY: Before Binary, Before Computers
1940s: The Frustration That Started Everything
The Problem:
Engineers building early computers were furious. They needed to store numbers, but they only had electricity to work with.
The Constraint:

Electricity has only 2 states: ON or OFF
Light bulb: ON or OFF
Switch: UP or DOWN

The Question That Changed Everything:
"How do we count and store numbers when we only have ON/OFF switches?"

💡 THE BREAKTHROUGH: The Light Bulb Revelation
Imagine ONE Light Bulb:
💡 OFF = 0
💡 ON  = 1
How many different values can you represent?

Answer: 2 values (0 and 1)

That's it. One switch = 2 possibilities.

Now Add ANOTHER Light Bulb:
Bulb 1    Bulb 2    What number?
  OFF       OFF         0
  OFF       ON          1
  ON        OFF         2
  ON        ON          3
How many different values now?

Answer: 4 values (0, 1, 2, 3)

The Pattern Emerges:

1 bulb = 2 possibilities (2^1)
2 bulbs = 4 possibilities (2^2)
3 bulbs = 8 possibilities (2^3)


🔢 WHY POWER OF 2? The Multiplication Discovery
Think About Choices:
With 1 switch:

Choice 1: OFF or ON → 2 choices

With 2 switches:

First switch: OFF or ON → 2 choices
Second switch: OFF or ON → 2 choices
Total combinations: 2 × 2 = 4 choices

With 3 switches:

2 × 2 × 2 = 8 choices

With 8 switches:

2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 = 256 choices

This is WHY we say 2^8:

It's just shorthand for "multiply 2 by itself 8 times"
2^8 = 256


🏗️ THE 8-BIT BUILDING: Why They Chose 8 Switches
1970s: The Byte Is Born
The Problem:
Engineers needed a standard "chunk size" for computers.
Why 8 switches (8 bits)?

Too Small (4 bits): Only 16 values (0-15) - not enough!
Too Large (16 bits): Wasteful, hardware was expensive
Just Right (8 bits): 256 values (0-255) - perfect for letters, numbers, symbols!

They called this 8-bit chunk a "BYTE"

🎯 YOUR CONFUSION SOLVED: The Math
Let me clear up your specific questions:
Question: "Why is 1 bit 4?"
Answer: 1 bit is NOT 4! Let me show you:
1 bit  = 2 possibilities (2^1 = 2)
2 bits = 4 possibilities (2^2 = 4)
3 bits = 8 possibilities (2^3 = 8)
4 bits = 16 possibilities (2^4 = 16)
8 bits = 256 possibilities (2^8 = 256)

Question: "8 bits should be 8×4 = 32?"
Answer: NO! You don't multiply bits by 4!
The Formula Is:

Number of possibilities = 2^(number of bits)

For 8 bits:

NOT 8 × 4 = 32 ❌
BUT 2^8 = 256 ✅

Why 2^8?
Because each bit doubles your possibilities:

1 bit: 2
2 bits: 2 × 2 = 4
3 bits: 2 × 2 × 2 = 8
8 bits: 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 = 256


Question: "Each 8-bit chunk is 32 bits?"
Answer: NO! Let me clarify:
1 chunk (called an "octet" or "byte") = 8 bits
An IP address has 4 chunks:
192  .  168  .  1   .  10
↑       ↑       ↑      ↑
8 bits  8 bits  8 bits 8 bits

Total: 8 + 8 + 8 + 8 = 32 bits

Question: "IP has 0.0.0.0, so we have 32×4 = 128 bits?"
Answer: NO! You're counting wrong:
An IP has 4 numbers separated by dots:

Each number = 8 bits
4 numbers = 4 × 8 = 32 bits total

NOT 32 × 4!

Question: "So why does it go to 255?"
Answer: Because with 8 light switches, the MAXIMUM you can represent is 255!
Let me prove it:
Switch #: 8    7    6    5    4    3    2    1
Position: 128 +64 +32 +16 + 8 + 4 + 2 + 1

ALL SWITCHES ON:
128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 255
But wait, you can also have ALL SWITCHES OFF = 0
So with 8 bits you can represent:

Minimum: 0 (all OFF)
Maximum: 255 (all ON)
Total values: 256 (from 0 to 255)


🔥 THE COMPLETE JOURNEY: How We Got IP Addresses
Chapter 1: The Switch Problem (1940s)
Engineers: "We only have ON/OFF switches. How do we count?"
Solution: Use multiple switches! Each switch position represents a power of 2.

Chapter 2: The Byte Is Born (1960s)
Engineers: "How many switches should we group together?"
They tried:

4 switches (4 bits) = 0 to 15 → Too small!
16 switches (16 bits) = 0 to 65,535 → Too big for 1960s hardware!

Solution: 8 switches (8 bits) = 0 to 255 → Perfect!
They called this a BYTE (or OCTET in networking).

Chapter 3: The Internet Is Born (1981)
Problem: Computers need addresses to find each other!
Question: How long should an address be?
Decision:

Use 4 bytes (4 groups of 8 bits)
Total: 32 bits
This gives us 2^32 = 4.3 billion addresses

Why 4 bytes?

Easy for humans to read: 192.168.1.10
Each byte (0-255) fits in human brain easily
4 billion addresses seemed infinite in 1981 (they were wrong!)


Chapter 4: CIDR Is Invented (1993)
Problem: The internet was running out of addresses!
The Old System (Before CIDR):
Networks came in only 3 sizes:

Class A: 16 million addresses (way too big!)
Class B: 65,000 addresses
Class C: 254 addresses (way too small!)

Example of the waste:

Company needs 1,000 addresses
Gets Class B with 65,000 addresses
Wastes 64,000 addresses!

The Frustration:
It's like going to a store:

You need a small bag (1,000 items)
Store only sells tiny bags (254 items) or HUGE bags (65,000 items)
You're forced to buy the huge bag and waste space!


The CIDR Revolution:
Genius Idea: "What if we could cut networks to ANY size we want?"
The Solution: CIDR Notation
Instead of fixed sizes, use a "/" number to say "how many bits are locked":
192.168.1.0/24

The /24 means:
"Lock the first 24 bits for the network"
"Leave the last 8 bits for hosts"

24 locked bits = 8 flexible bits
8 flexible bits = 2^8 = 256 addresses
256 - 2 (network & broadcast) = 254 usable addresses

🎯 CIDR EXPLAINED: The Knife That Cuts Networks
What CIDR Actually Is:
CIDR = A way to say "how many bits are locked"
Think of it as a precision knife that cuts the 32-bit address:
IP Address: 192.168.1.0/24

Binary: 11000000.10101000.00000001.00000000
        |-------24 bits locked-------|8 bits free|
        
/24 means: "Cut after bit 24"

CIDR Examples:
Example 1: /24
192.168.1.0/24
- Locked: 24 bits (network address)
- Free: 8 bits (for hosts)
- Hosts: 2^8 = 256 total, 254 usable
Example 2: /30
10.0.0.0/30
- Locked: 30 bits (network address)
- Free: 2 bits (for hosts)
- Hosts: 2^2 = 4 total, 2 usable
Example 3: /16
172.16.0.0/16
- Locked: 16 bits (network address)
- Free: 16 bits (for hosts)
- Hosts: 2^16 = 65,536 total, 65,534 usable

🧮 THE POWER OF 2 MYSTERY: Why Each Bit Position Doubles
Let Me Show You Physically:
Imagine you're lining up people for a photo:
With 1 position:

Person can stand LEFT or RIGHT
2 possibilities

With 2 positions:

Position 1: LEFT or RIGHT (2 choices)
Position 2: LEFT or RIGHT (2 choices)
Total combinations: 2 × 2 = 4

L-L
L-R
R-L
R-R
With 3 positions:

2 × 2 × 2 = 8 combinations

With 8 positions (8 bits):

2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 = 256 combinations

This is WHY each bit position is a power of 2!

The Switch Value Pattern:
Why does each switch have these specific values?
Position 1 (rightmost): Worth 1    (2^0 = 1)
Position 2:             Worth 2    (2^1 = 2)
Position 3:             Worth 4    (2^2 = 4)
Position 4:             Worth 8    (2^3 = 8)
Position 5:             Worth 16   (2^4 = 16)
Position 6:             Worth 32   (2^5 = 32)
Position 7:             Worth 64   (2^6 = 64)
Position 8 (leftmost):  Worth 128  (2^7 = 128)
Why these values? Each position is worth DOUBLE the previous:

1, 2, 4, 8, 16, 32, 64, 128

Because: When you have 2 choices at each position, each new position doubles your counting power!

✅ FINAL CLARITY: The Complete Picture
The Truth About Bits and Bytes:
1 BIT    = 1 switch    = 2 values (0 or 1)
2 BITS   = 2 switches  = 4 values (0-3)
4 BITS   = 4 switches  = 16 values (0-15)
8 BITS   = 8 switches  = 256 values (0-255) ← Called a BYTE/OCTET
32 BITS  = 32 switches = 4.3 billion values
IP Address Structure:
192    .   168   .   1     .   10
8 bits     8 bits   8 bits     8 bits
(0-255)    (0-255)  (0-255)    (0-255)

Total: 4 × 8 = 32 bits
CIDR Notation:
/24 = "First 24 bits are network, last 8 bits are hosts"
/16 = "First 16 bits are network, last 16 bits are hosts"
/30 = "First 30 bits are network, last 2 bits are hosts"

LEVEL 1: IANA's Master Registry
IANA maintains the "Constitution" - the master allocation table:
┌─────────────────────────────────────────┐
│ IANA MASTER REGISTRY                    │
├─────────────────────┬───────────────────┤
│ IP Range            │ Allocated To      │
├─────────────────────┼───────────────────┤
│ 0.0.0.0/8           │ Reserved          │
│ 1.0.0.0/8           │ APNIC             │
│ 2.0.0.0/8           │ RIPE NCC          │
│ 8.8.0.0/16          │ Google            │
│ 17.0.0.0/8          │ Apple             │
│ 20.0.0.0/8          │ Microsoft         │
│ 73.0.0.0/8          │ ARIN              │
│ ...                 │ ...               │
└─────────────────────┴───────────────────┘


!

🔍 HOW THEY KNOW IF AN IP IS USED: The Real-Time Tracking
Method 1: DHCP Lease Database
Your ISP runs a DHCP server (Dynamic Host Configuration Protocol):
Think of it as a HOTEL CHECK-IN SYSTEM:

Guest checks in → Gets room 301 → Logged in system
Guest checks out → Room 301 marked available
New guest → Gets room 301 → Logged again

Same with IPs:
You connect → Get 73.142.56.89 → Logged
You disconnect → IP marked available  
New customer → Gets 73.142.56.89 → Logged

The DHCP Lease Table (Live Tracking):
┌─────────────────────────────────────────────────────────┐
│ IP             │ Status    │ Lease Start │ Lease End   │
├─────────────────────────────────────────────────────────┤
│ 73.142.56.89   │ LEASED    │ 14:30 Mon   │ 14:30 Tue   │
│ 73.142.56.90   │ AVAILABLE │ -           │ -           │
│ 73.142.56.91   │ LEASED    │ 09:15 Mon   │ 09:15 Tue   │
│ 73.142.56.92   │ RESERVED  │ (Static)    │ (Static)    │
└─────────────────────────────────────────────────────────┘
Real-Time Updates:

Every second, the system checks: "Is this lease expired?"
Customer disconnects → Lease ends → IP goes back to pool
New customer connects → System assigns next available IP
IMPOSSIBLE for duplicates - database prevents it!


Method 2: ARP Tables (Local Network Tracking)
Your router maintains an ARP table (Address Resolution Protocol):
┌─────────────────────────────────────────────┐
│ Local Network: Who's Currently Connected?   │
├──────────────────┬──────────────────────────┤
│ IP Address       │ MAC Address (Device ID)  │
├──────────────────┼──────────────────────────┤
│ 192.168.1.1      │ Router itself            │
│ 192.168.1.10     │ AA:BB:CC:11:22:33 (Laptop)│
│ 192.168.1.11     │ DD:EE:FF:44:55:66 (Phone) │
│ 192.168.1.12     │ 11:22:33:AA:BB:CC (TV)    │
└──────────────────┴──────────────────────────┘
How it prevents duplicates:

Device requests IP 192.168.1.10
Router checks ARP table: "Is 192.168.1.10 taken?"
If YES → Router says "NO, try 192.168.1.13"
If NO → Router assigns it and logs it


This is PUBLIC! You can see it at: https://www.iana.org/assignments/ipv4-address-space/

Reserved Address 1: Network Address
Example: 192.168.1.0
Purpose: Identifies the network itself
Cannot assign to devices!

Reserved Address 2: Broadcast Address  
Example: 192.168.1.255
Purpose: Send message to ALL devices
Cannot assign to devices!

Usable Range: 192.168.1.1 to 192.168.1.254
Total Usable: 254 IPs

The Solution:
"What if we had ONE central box that just repeats everything?"
        [HUB]
      /   |   \
   [PC1][PC2][PC3]
How a Hub Works:
PC1 sends message: "Hello PC2!"
Hub: "I'M DUMB! I'LL SHOUT THIS TO EVERYONE!"
→ PC2 hears it: "That's for me!" ✓
→ PC3 hears it: "Not for me..." (ignores)
→ PC4 hears it: "Not for me..." (ignores)


How a Switch Works:
        [SWITCH]
         /  |  \
      [PC1][PC2][PC3]
The Switch's Brain (MAC Address Table):
┌────────────┬─────────────────────┐
│ Port       │ MAC Address         │
├────────────┼─────────────────────┤
│ Port 1     │ AA:BB:CC:DD:EE:01  │ ← PC1
│ Port 2     │ 11:22:33:44:55:66  │ ← PC2
│ Port 3     │ FF:EE:DD:CC:BB:AA  │ ← PC3
└────────────┴─────────────────────┘


Routes Table:
default => 192.168.0.254
Translation:
"Machine B says: If I want to reach ANYTHING outside my immediate network, send it to 192.168.0.254 (the router's gateway)"

What "Host" Means:

Host = Any end device (computer, phone, printer, server)
It's called "host" because it "hosts" applications and users
NOT a router, NOT a switch - just a regular computer!

INTERFACE B1
What "Interface" Means:

Interface = A network port (the physical/virtual plug)
Every network connection has an interface
Like having multiple doors on a house!


🚫 CRITICAL CONSTRAINTS: What Each Device CAN'T Do
HUB:

❌ Can't learn addresses
❌ Can't prevent collisions
❌ Can't provide privacy
❌ Can't connect different networks
✅ Only thing it does: Repeat signals to ALL ports
Status: EXTINCT (dead since 1990s)

SWITCH:

✅ Learns MAC addresses
✅ Prevents collisions
✅ Provides privacy
❌ CAN'T connect different networks!
❌ Only works with ONE network (same IP range)
Use: Connect devices in SAME network

ROUTER:

✅ Connects DIFFERENT networks
✅ Routes between IP ranges
✅ Has multiple interfaces (dual citizenship)
✅ Makes routing decisions
❌ More expensive than switches
❌ Slower than switches (more processing)
Use: Connect DIFFERENT networks together


What does DEFAULT mean?"
DEFAULT = Your fallback plan when you don't know what else to do!
Computer's logic:
if (destination in my network):
    send directly
else if (specific route exists):
    use that route
else:
    use DEFAULT route ← "When lost, go here!"

✅ THE COMPLETE MENTAL MODEL
Hub (Dead): Dumb megaphone, shouts to everyone
Switch: Smart mailman, learns addresses, connects devices in SAME network
Router: Border checkpoint, has dual citizenship, connects DIFFERENT networks
Interface: A door/port on a device
Default Route: Emergency contact when you don't know where to send data


NAT = Network Address Translation


🔢 PORT NUMBERS: The Apartment Numbers
Why NAT Needs Port Numbers:
The Problem:
You have: ONE public IP (73.142.56.89)
You have: 10 devices all using internet

How does router know which response goes to which device?
The Solution: PORT NUMBERS!
Port Number = 16-bit number (0-65535)

Range breakdown:
0-1023:     Well-known ports (HTTP=80, HTTPS=443, DNS=53)
1024-49151: Registered ports (specific applications)
49152-65535: Dynamic ports (NAT uses these!)

NAT Port Mapping:
Device 1 (192.168.1.10) → NAT Port 49152
Device 2 (192.168.1.11) → NAT Port 49153  
Device 3 (192.168.1.12) → NAT Port 49154
...

All share same public IP: 73.142.56.89
But different ports: 49152, 49153, 49154...

Internet sees:
- 73.142.56.89:49152 (thinks it's one device)
- 73.142.56.89:49153 (thinks it's another device)
- 73.142.56.89:49154 (thinks it's another device)

Actually: All same public IP, different devices!

What is IP?
IP is a connectionless protocol that operates at the network layer of the OSI model. IP enables communication between hosts by carrying data within packets. Each host is assigned an IP address which is used to ensure that traffic is sent to the correct destination, synonymous in many ways to a postal address that we place on a letter.

Addressing
An IP address (in the case of v4) is built upon 32-bits, expressed in four numbers known as octets. Each octet is 8 bits i.e one byte.



Each address is made up of 2 identifiers (shown below):

Network - the network the IP address belongs to. For example the street name.
Host - the host identifier of the device for the network. For example the house number.

CIDR/VLSM
With the explosion of the internet and the need to address more and more devices, this issue was compounded and a solution was required.

The solution to this issue came in the form of - Classless Inter-Domain Routing (CIDR) and Variable Length Subnet Masking (VLSM). Both of which are key to modern day subnetting.

Variable Length Subnet Masking (VLSM)
VLSM is the "subnetting of subnets," which means that VLSM allows network engineers to divide an IP address space into a hierarchy of subnets of different sizes, making it possible to create subnets with very different host counts without wasting large numbers of addresses.[1]


Subnetting Overview
First of all - what is subnetting?

A subnetwork or subnet is a logical subdivision of an IP network.The practice of dividing a network into two or more networks is called subnetting.[2]

Given: IP = X.X.X.Y and Mask = 255.255.255.M

Step 1: Block Size
Block = 256 - M

Step 2: Network Start
Network = (Y ÷ Block) × Block
(Take integer part of division!)

Step 3: Network Range
Start: Network
End: Network + Block - 1

Step 4: Usable IPs
Start + 1 to End - 1
(Skip first and last!)


IP: 112.227.118.132
Mask: 255.255.255.128

Step 1: Block Size
256 - 128 = 128

Step 2: Network Start  
132 ÷ 128 = 1.03... → 1
1 × 128 = 128

Step 3: Range
Start: 128
End: 128 + 128 - 1 = 255

Step 4: Usable
129 to 254

Pick any from: 129, 130, 131, 132, 133... 254


IP: 112.227.118.132
Mask: 255.255.255.192

Step 1: Block size
256 - 192 = 64

Step 2: Network start
132 ÷ 64 = 2.06... → 2
2 × 64 = 128

Network: 112.227.118.128/26
Range: 112.227.118.128 - 112.227.118.191
Usable: 112.227.118.129 - 112.227.118.190


Calculations 3 Methods:
1- CIDR calculations with bits
2- Magic Number.
3- Block size calculations


Given:
IP: 112.227.118.132
Mask: 255.255.255.128 (/25)

Step 1: Calculate MY network range
Block size: 256 - 128 = 128
Network start: 132 ÷ 128 = 1 → 1 × 128 = 128
Range: 128 to 255

Step 2: Check if target IP is in range
Target: 112.227.118.133

Question: Is 133 between 128 and 255?
Visual: 128 ... 132 ... 133 ... 255
         ↑           ↑
      Start     Target is HERE!

Answer: YES! ✅


Method 3: The Binary AND (What Computers Do)
My IP: 112.227.118.132
Binary: 01110000.11100011.01110110.10000100

My Mask: 255.255.255.128
Binary: 11111111.11111111.11111111.10000000

AND Operation:
01110000.11100011.01110110.10000100 (My IP)
11111111.11111111.11111111.10000000 (Mask)
─────────────────────────────────────
01110000.11100011.01110110.10000000 = 112.227.118.128 (MY network)

Now check target:
Target IP: 112.227.118.133
Binary: 01110000.11100011.01110110.10000101

AND with MY mask:
01110000.11100011.01110110.10000101 (Target)
11111111.11111111.11111111.10000000 (My mask)
─────────────────────────────────────
01110000.11100011.01110110.10000000 = 112.227.118.128 (SAME network!)

Result: Same network = LOCAL! ✅


📐 THE MAGIC NUMBER FORMULA
The Single Most Important Formula:
Magic Number = 256 - (Last Octet of Subnet Mas

CIDR: /28
Subnet Mask: 255.255.255.240

Step 1: Find magic number
Last octet: 240
Magic Number: 256 - 240 = 16

Step 2: What does 16 mean?
- Each network has 16 addresses
- Networks jump by 16
- Network boundaries: 0, 16, 32, 48, 64, 80...



🎯 THE THREE METHODS COMPARED
Method 1: MAGIC NUMBER (Fastest!)
Given: 192.168.1.50/26

Step 1: Magic number
256 - 192 = 64

Step 2: Find network
50 ÷ 64 = 0.78... → 0
0 × 64 = 0
SSS
Network: 192.168.1.0/26
Range: 0-63

Time: 5 seconds! ⚡

Method 2: BINARY (Most Accurate)
Given: 192.168.1.50/26

IP: 192.168.1.50
Binary: 11000000.10101000.00000001.00110010

Mask: 255.255.255.192
Binary: 11111111.11111111.11111111.11000000

AND operation:
00110010 (50)
11000000 (192)
────────
00000000 (0)

Network: 192.168.1.0/26

Time: 2 minutes 🐌

Method 3: VISUAL RANGE (Good for Checking)
Given: 192.168.1.50/26

Step 1: Know boundaries
/26 = 64 addresses
Networks: 0-63, 64-127, 128-191, 192-255

Step 2: Visual placement
Is 50 in:
0-63? YES! ✅

Network: 192.168.1.0/26

Time: 10 seconds ⏱️


Two Parts:
1. DESTINATION (left side):

"Which network am I trying to reach?"
Can be specific network (129.53.190.0/24)
Or "default" (everything else)

2. GATEWAY (right side after =>):

"Which router interface should I send to?"
Must be an IP address
Must be in MY local network (reachable directly!)


- - - - - - - - - - - - - - - - - - - - - - - -





https://www.youtube.com/watch?v=POPoAjWFkGg
https://www.youtube.com/watch?v=eHV1aOnu7oM
https://www.youtube.com/watch?v=sMHzfigUxz4
https://www.youtube.com/watch?v=7_LPdttKXPc
https://www.youtube.com/watch?v=1z0ULvg_pW8
https://www.youtube.com/watch?v=gQtgtKtvRdo&t=77s
https://www.youtube.com/watch?v=kyMoEgdMbH8
https://www.youtube.com/watch?v=bdNS0K4Bt8U
https://www.youtube.com/watch?v=6_giEv20En0
https://www.youtube.com/watch?v=_ifRgCb8o60
https://github.com/ricardoreves/42-net-practice (Please review this at the end so it doesn't take from the pleasure of searching)
https://www.softwaretestinghelp.com/subnet-mask-and-network-classes/
https://www.rfc-editor.org/rfc/rfc5414.html
https://www.iana.org/
https://whois.arin.net/rest/ip/212.118.12.219?s=212.118.12.219
https://www.abuseipdb.com/check/212.118.12.219
https://www.google.com/search?sca_esv=55d2a26e7ed4668f&sxsrf=AE3TifOthiAbelTQGsocGBiKNQm-QVzhRw:1763816193827&udm=2&fbs=AIIjpHxU7SXXniUZfeShr2fp4giZ1Y6MJ25_tmWITc7uy4KIeuYzzFkfneXafNx6OMdA4MQRJc_t_TQjwHYrzlkIauOK_IaFSQcTHs2AgJbmYqOLNr-gBKF7I3dfcWHoQ8Rv9DjgCkddkmI70Eyfx6YeKCiQpQ6vp-564Wh7Ux48nEGedWNIKpMOjgODVmfE1geG6VKILIklDXLwRh1QTq_557DgED4jgQ&q=dhcp&sa=X&ved=2ahUKEwiM47mt54WRAxVbLPsDHbjjKTUQtKgLegQIERAB&biw=1920&bih=846&dpr=1
https://www.youtube.com/watch?v=Glb88drqrOg
https://www.youtube.com/watch?v=ddM9AcreVqY&list=PLavxF_EKV9wvkqAXgMQdcnv8eGPQIYqSe
https://www.packetcoders.io/a-beginners-guide-to-subnetting/
https://en.wikipedia.org/wiki/Broadcast,_unknown-unicast_and_multicast_traffic?ref=packetcoders.io
https://github.com/lpaube/NetPractice?tab=readme-ov-file#subnet-mask
ASK CLAUDE
