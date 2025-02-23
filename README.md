To create and test a switch, we used the following steps:

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
Apoi am implementat logica pentru STP prezentata in cerinta si am completat sa functioneze si peste forward. 
