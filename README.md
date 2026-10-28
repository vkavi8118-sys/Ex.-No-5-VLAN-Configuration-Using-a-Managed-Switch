## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date:28.10.2026
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
<img width="1920" height="1080" alt="Screenshot (248)" src="https://github.com/user-attachments/assets/f88178e0-9ed0-47f3-bbec-d9f8e9a50337" />

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
<img width="1920" height="1080" alt="Screenshot (247)" src="https://github.com/user-attachments/assets/5fec6d54-dc48-49dc-bc3f-5e0238eb7c7f" />

•	PC IP settings<br>
<img width="1920" height="1080" alt="Screenshot 2026-10-28 180028" src="https://github.com/user-attachments/assets/6db409ab-88c9-4c69-bc48-8143428df8b5" />


<img width="1920" height="1080" alt="Screenshot (246)" src="https://github.com/user-attachments/assets/87300cbe-21ba-46c5-b77a-739334e12583" />

•	Successful ping between PCs in the same VLAN<br>
<img width="687" height="330" alt="Screenshot 2026-10-28 180703" src="https://github.com/user-attachments/assets/0748231e-754b-47e6-8602-15ad3d3bbf47" />

<img width="712" height="570" alt="Screenshot 2026-10-28 175147" src="https://github.com/user-attachments/assets/4beba9a2-e4c8-436e-9f1b-315583eaac69" />


•	Failed ping between PCs in different VLANs<br>
<img width="745" height="330" alt="Screenshot 2026-10-28 180656" src="https://github.com/user-attachments/assets/a48698d5-c6e4-4184-b092-0614df5620ae" />

<img width="656" height="595" alt="Screenshot 2026-10-28 175035" src="https://github.com/user-attachments/assets/1a82c7a9-028c-484c-b3f2-1b3a1866e576" />

________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

