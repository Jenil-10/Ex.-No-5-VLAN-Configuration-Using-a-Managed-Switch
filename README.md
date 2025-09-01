## Ex. No: 4  VLAN Configuration Using a Managed Switch
Date:1/8/25
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2b094644-dc5a-4bf2-a6be-3214bfe30b96" /><br>
________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br>
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>
________________________________________
# Output (Screenshots)
•	VLAN configuration on switch<br>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7bb1ae40-f60a-4689-bbe4-65b4a7de06d3" />
•	PC IP settings<br>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3ac02328-1a71-47da-bd00-bd923b268155" />

•	Successful ping between PCs in the same VLAN<br>
<img width="1920" height="1080" alt="Screenshot 2025-09-01 141327" src="https://github.com/user-attachments/assets/39a1758f-f00c-4b40-876a-d73f90fe03dc" />

•	Failed ping between PCs in different VLANs<br>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/68f03f0a-e676-4336-8733-358be01d7346" />


________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

