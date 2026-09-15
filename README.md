# Ex. No: 12 – Packet Tracer: Use Ping and Traceroute to Test Network Connectivity

# Date: 11/09/2026

## NAME: SANJEEV.R

## REG NO: 212224060235
________________________________________<br>

# Objective:

To test and restore IPv4 and IPv6 network connectivity using diagnostic commands (ping and tracert), identify faults, and verify proper routing between end devices in a dual-stack (IPv4 + IPv6) topology.<br>
Tasks:<br>
•	Use ipconfig and ipv6config to collect addressing information.<br>
•	Use ping and tracert to test connectivity.<br>
•	Locate and fix connectivity issues.<br>
•	Verify successful restoration of both IPv4 and IPv6 communication.<br>
________________________________________<br>

# Apparatus / Tools Required:

• Cisco Packet Tracer<br>
• 3 Routers (R1, R2, R3 – 2911 or equivalent)<br>
• 4 PCs (PC1–PC4)<br>
• Copper straight-through and serial DCE/DTE cables<br>
________________________________________<br>

# Network Topology Diagram:

<img width="1920" height="1080" alt="Screenshot 2026-09-11 124031" src="https://github.com/user-attachments/assets/909a0ceb-ec1b-4ee7-ac2e-2210fb070504" />

________________________________________<br>

Addressing Table<br>
Device	Interface	IPv4 Address / Subnet Mask	IPv6 Address / Prefix	Default Gateway<br>
R1	G0/0	10.10.1.97 / 255.255.255.224	2001:db8:1:1::1/64	N/A<br>
R1	S0/0/1	10.10.1.6 / 255.255.255.252	2001:db8:1:2::2/64	N/A<br>
R2	S0/0/0	10.10.1.5 / 255.255.255.252	2001:db8:1:2::1/64	N/A<br>
R2	S0/0/1	10.10.1.9 / 255.255.255.252	2001:db8:1:3::1/64	N/A<br>
R3	G0/0	10.10.1.17 / 255.255.255.240	2001:db8:1:4::1/64	N/A<br>
R3	S0/0/1	10.10.1.10 / 255.255.255.252	2001:db8:1:3::2/64	N/A<br>
PC1	NIC	(DHCP/Manual IPv4)	(Auto IPv6)	R1 G0/0<br>
PC2	NIC	(DHCP/Manual IPv6)	(Auto IPv6)	R1 G0/0<br>
PC3	NIC	(DHCP/Manual IPv4)	(Auto IPv6)	R3 G0/0<br>
PC4	NIC	(DHCP/Manual IPv6)	(Auto IPv6)	R3 G0/0<br>
________________________________________<br>

# Procedure for Students – Use Ping and Traceroute (13.2.7):

Download the Activity File<br>
Ensure the file 13.2.7-packet-tracer---use-ping-and-traceroute-to-test-network-connectivity.pka is saved in an accessible folder (e.g., Downloads or Documents).<br>
________________________________________

# Open Cisco Packet Tracer:

Launch Cisco Packet Tracer → Click File → Open...<br>
Select the .pka file and click Open.<br>
________________________________________<br>

# Start the Activity:

The pre-configured topology (R1–R3 and PCs PC1–PC4) will load automatically.<br>
Follow the right-hand Instruction Panel for activity steps.<br>
________________________________________

# Part 1: Test and Restore IPv4 Connectivity<br>:

# Step 1: Verify IPv4 Configuration<br>

1.	Click PC1, open Command Prompt, and type:<br>
2.	ipconfig /all<br>
Note IPv4 address, mask, and gateway.<br>
3.	Repeat on PC3 and record data in the Addressing Table.<br>
________________________________________<br>

# Step 2: Test and Locate IPv4 Issues:

1.	From PC1, ping PC3:<br>
2.	ping <PC3 IPv4 address><br>
Observe failure (expected).<br>
3.	From PC1, trace the route:<br>
4.	tracert <PC3 IPv4 address><br>
Record the last reachable hop.<br>
5.	Repeat the same from PC3 to PC1.<br>
________________________________________<br>

# Step 3: Analyze and Diagnose

•	On R1, run:<br>
•	show ip interface brief<br>
•	show ip route<br>
Identify incorrect interfaces or missing routes.<br>
•	Repeat on R2 and R3.<br>
Compare configurations with documentation to locate the misconfigured interface or subnet.<br>
________________________________________<br>

# Step 4: Implement Fix

Reconfigure the faulty interface or routing entry. Example:<br>
configure terminal<br>
interface s0/0/1<br>
 ip address 10.10.1.6 255.255.255.252<br>
 no shutdown<br>
end<br>
copy running-config startup-config<br>
________________________________________<br>

# Step 5: Verify IPv4 Restoration

From PC1:<br>
ping <PC3 IPv4 address><br>
From PC3:<br>
ping <PC1 IPv4 address><br>
Both pings should now succeed.<br>
________________________________________

# Part 2: Test and Restore IPv6 Connectivity

# Step 1: Verify IPv6 Configuration

On PC2 and PC4, use:<br>
ipv6config /all<br>
Record IPv6 address, prefix, and gateway.<br>
________________________________________

# Step 2: Test and Trace IPv6 Connectivity

1.	From PC2, ping PC4:<br>
2.	ping 2001:db8:1:4::a<br>
Expected: Failure initially.<br>
3.	Trace route:<br>
4.	tracert 2001:db8:1:4::a<br>
Record last reachable IPv6 address.<br>
________________________________________

# Step 3: Diagnose and Correct IPv6 Faults

•	On routers, use:<br>
•	show ipv6 interface brief<br>
•	show ipv6 route<br>
Verify that interfaces are up and prefixes match documentation.<br>
•	Identify and correct errors (e.g., missing IPv6 address, shutdown interface).<br>
________________________________________

# Step 4: Implement and Verify IPv6 Restoration

1.	Correct any configuration errors using CLI.<br>
2.	Confirm end-to-end IPv6 connectivity with ping and tracert.<br>
________________________________________

# Verification and Testing Summary

Command	Purpose<br>
ipconfig /all	View IPv4 details<br>
ipv6config /all	View IPv6 details<br>
ping	Test reachability<br>
tracert	Trace route hops<br>
show ip interface brief	Verify IPv4 interface status<br>
show ipv6 interface brief	Verify IPv6 interface status<br>

________________________________________

# Output (Attach Screenshots)

• Command outputs (ipconfig, ipv6config, ping, tracert) for PCs.<br>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/542760d5-083a-48fd-b1b4-2aad88ac7f09" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/affaf3a9-6d49-4485-abcf-f7359a0bdbc7" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ad91c2ae-10fa-4ec3-bc99-c9494cb3bdaf" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/05f3822f-a729-4770-b6db-c45bdb4670c2" />





• Router interface and routing tables.<br>

<img width="1920" height="1080" alt="Screenshot 2026-09-11 104447" src="https://github.com/user-attachments/assets/bb091d93-a0c6-4e5d-928d-5b7b893ddcc7" />

<img width="1920" height="1080" alt="Screenshot 2026-09-11 105529" src="https://github.com/user-attachments/assets/0c7ac7f2-283c-45bb-a511-44589e7be6a5" />

<img width="1920" height="1080" alt="Screenshot 2026-09-11 104716" src="https://github.com/user-attachments/assets/6c6fd775-db6c-4d01-9f02-0b2e18ac9b58" />




• Successful ping results after fixes.<br>

<img width="1920" height="1080" alt="Screenshot 2026-09-11 120355" src="https://github.com/user-attachments/assets/9e6c7eda-4680-47a0-b21d-dfbf224dc6e3" />

<img width="1920" height="1080" alt="Screenshot 2026-09-11 120427" src="https://github.com/user-attachments/assets/8e48eb46-309a-4e25-b98f-7a834eaef015" />

<img width="1920" height="1080" alt="Screenshot 2026-09-11 120411" src="https://github.com/user-attachments/assets/0e5da855-fbb7-4adb-961b-3c8cf15e4e49" />

<img width="1920" height="1080" alt="Screenshot 2026-09-11 120522" src="https://github.com/user-attachments/assets/33b02f5c-f43b-4bcf-b2b4-ab319c1277ba" />

________________________________________<br>

# Result:

IPv4 and IPv6 connectivity issues were diagnosed and resolved using ping and tracert commands. Routers and PCs achieved full dual-stack communication after correcting configuration errors, confirming network restoration and routing accuracy.<br>

