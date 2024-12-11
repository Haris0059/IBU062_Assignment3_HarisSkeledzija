List of all devices being used (first one is Name of Device and second one is a model of a device being used):
- Router0 (2811): 168.90.0.1 and 210.3.14.1
- Switch0 (2960-24TT)
- Switch1 (2960-24TT)
- PC0 (PC-PT) 168.90.0.2
- PC1 (PC-PT) 168.90.0.3
- PC2 (PC-PT) 210.3.14.2
- Laptop0 (Laptop-PT) 168.90.0.4
- Server0 (Server-PT) 168.90.0.5
- Server1 (Server-PT) 210.3.14.3
- Server2 (Server-PT) 210.3.14.4
- PC3 (PC-PT) 168.90.0.6
- PC4 (PC-PT) 210.3.14.5

DHCP Commands used inside of Router's CLI:
 1. Enter a configuration mode:
 ```bash
 en 
 configure terminal
 ```

2. Assign a IP to Router (First Switch):
```bash
interface  Fa0/0
ip add 168.90.0.1 255.255.0.0
no shutdown
exit
```

3. Assign a IP to Router (Second Switch):
```bash
interface  Fa0/1
ip add 210.3.14.1 255.255.255.0
no shutdown
exit
```

4. Configure DHCP for First Switch:
```bash
ip dhcp pool SWITCH1_POOL
network 168.90.0.0 255.255.0.0
default-router 168.90.0.1
```

5. Configure DHCP for Second Switch:
```bash
ip dhcp pool SWITCH2_POOL
network 210.3.14.0 255.255.255.0
default-router 210.3.14.1
```

6. Exclude Router IP Addressess from DHCP
```bash
ip dhcp excluded-address 168.90.0.1
ip dhcp excluded-address 210.3.14.1
```