# 🖧 Switch

This project simulates a **network switch** implemented in **Python**, allowing packet switching, VLAN management, and Spanning Tree Protocol (STP) support. The switch learns MAC addresses dynamically and forwards packets efficiently while avoiding loops using STP.

## 🌐 Features

- **MAC Address Learning** – Uses a CAM (Content Addressable Memory) table to store MAC-to-port mappings.
- **Packet Forwarding** – If the destination MAC is known, the switch forwards the packet to the corresponding port; otherwise, it broadcasts.
- **VLAN Support** – Implements Virtual LANs to segment network traffic.
- **Spanning Tree Protocol (STP)** – Prevents network loops using BPDU (Bridge Protocol Data Units).
- **ICMP Testing** – Allows communication testing between hosts via `ping`.
- **Wireshark Debugging** – Supports packet capture for analysis.

## 🏗 Implementation Details

- **CAM Table Management** – Automatically updates mappings of MAC addresses to switch ports.
- **Packet Forwarding Logic**:
  - If the MAC address is known → Forward to specific port.
  - If unknown → Broadcast to all ports except the incoming one.
- **VLAN Management**:
  - Maintains a `vlan_table` to define trunk and access ports.
  - Handles tagged and untagged traffic based on VLAN rules.
- **Spanning Tree Protocol (STP) Implementation**:
  - Uses an `stp_table` with states: `Listening (L)`, `Blocking (B)`.
  - Implements BPDU message exchange for loop prevention.
  - Ensures STP rules are applied during packet forwarding.

## 🔧 Technology Stack

- **Python** – Core language for implementation.
- **Wireshark** – Packet analysis and debugging.
- **ICMP (ping)** – Used for basic connectivity testing.

## 🛠 Running the Simulation

Follow these steps to run the switch simulation:

### Start the Topology
```bash
sudo python3 checker/topo.py
```
This will open **9 terminals**:
- **6 host terminals** (host0 to host5)
- **3 switch terminals** (switch0 to switch2)

### Start the Switches
```bash
make run_switch SWITCH_ID=X  # X is 0, 1, or 2
```

### Host IP Addresses
| Host  | IP Address    |
|-------|--------------|
| host0 | 192.168.1.1  |
| host1 | 192.168.1.2  |
| host2 | 192.168.1.3  |
| host3 | 192.168.1.4  |
| host4 | 192.168.1.5  |
| host5 | 192.168.1.6  |

### Testing Connectivity
To test ICMP communication, run:
```bash
ping 192.168.1.2  # Example: From host0 to host1
```

### Debugging with Wireshark
For packet analysis, run:
```bash
wireshark&
```

## 💫 Contributing
Contributions are welcome! 🎉 If you have suggestions, improvements, or bug reports, feel free to open an issue or submit a pull request.

Let's collaborate to enhance the project! 🚀



<!-- To create and test a switch, we used the following steps:

## Running

```bash
sudo python3 checker/topo.py
```

This will open 9 terminals, 6 hosts and 3 for the switches. On the switch terminal you will run 

```bash
make run_switch SWITCH_ID=X # X is 0,1 or 2
```

The hosts have the following IP addresses.
```
host0 192.168.1.1
host1 192.168.1.2
host2 192.168.1.3
host3 192.168.1.4
host4 192.168.1.5
host5 192.168.1.6
```

We will be testing using the ICMP. For example, from host0 we will run:

```
ping 192.168.1.2
```

Note: We will use wireshark for debugging. From any terminal you can run `wireshark&`.


Descriere implementare RO:

Am implementat Procesul de comutare: am creat un cam_table care înregistrează mapările dintre adresele MAC și porturile prin care sunt accesibile. La recepția unui pachet, tabela se actualizează automat.
Dacă adresa MAC de destinație este cunoscută (există în tabelă), pachetul este trimis către portul asociat, altfel, daca nu se afla in tabela, pachetul est trimis broadcast.

Am implementat VLAN (Virtual Local Area Networks): am creat un vlan_table in care am "T" pentru trunk etc. 
Iar in functia forward am mai multe cazuri in care verific daca ambele sunt trunk sau daca unul este trunk si altul nu, sau daca nu sunt trunk-uri.(+functii de adaugare si stergere de taguri)

Am implementat STP (Spanning Tree Protocol): am creaat un stp_table in care am "L" pentru Listening, "B" pentru Blocking. Am completat functia send_bpdu in care am trimis BDPU.
Apoi am implementat logica pentru STP prezentata in cerinta si am completat sa functioneze si peste forward. -->



 
