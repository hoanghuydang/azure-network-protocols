<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- STEP 1: Create a Resource Group & two Virtual Machines (Windows 10 & Ubuntu Server 20.04)
- STEP 2: Observe ICMP Traffic
- STEP 3: Observe SSH Traffic
- STEP 4: Observe DHCP Traffic
- STEP 5: Observe DNS Traffic
- STEP 6: Observe RDP Traffic  

<h2>Actions and Observations</h2>

 <p>
<img src="https://i.imgur.com/sTqUBJf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/ZMXNHKq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 1: CREATE OUR RESOURCES</h2>

  - Create a Resource Group "RG-LabNP"
  - Create VM1 as a Windows 10 VM (create credentials)
  - Create VM2 as a Ubuntu Server 20.04 (create credentials)
</p>
<br />

 <p>
<img src="https://i.imgur.com/y3C5bi1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/QhQGJgn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/vbN8c2J.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/jQ0TCmC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/fpph90d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 2: OBSERVE ICMP TRAFFIC</h2>

  - Open Microsoft Remote Desktop and paste the Public IP Address of VM1 and continue to login using previous credentials
  - Open up the Browser in VM1 and google "download WireShark"
  - Once it is finished installing open up WireShark and filter for ICMP traffic only
  - Retrieve the private IP Address from the Ubuntu VM and attempt to ping it from within the Windows 10 VM
  - Attempt to Ping www.google.com and observe the traffic
  - Create perpetual ping (-t) from VM1 to VM2 and observe the traffic
  - Stop the pinging activity
</p>
<br />

 <p>
<img src="https://i.imgur.com/7609csE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/y04bJyP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/gNygHVs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 3: OBSERVE SSH TRAFFIC</h2>

  - Hop back into WireShark and filter for SSH traffic only
  - From the Windows 10 VM, "SSH into" your Ubuntu Virtual Machine (via its private IP address)
  - Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
  - Exit the SSH Connection by typing 'exit' and pressing Enter
</p>
<br />

 <p>
<img src="https://i.imgur.com/pOP5D0m.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 4: OBSERVE DHCP TRAFFIC</h2>

  - Go back to WireShark, filter for DHCP traffic only
  - From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
  - Observe the DHCP traffic being shown in WireShark
</p>
<br />

 <p>
<img src="https://i.imgur.com/7hxi4Rc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 <p>
<img src="https://i.imgur.com/GACnWeF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 5: OBSERVE DNS TRAFFIC</h2>

  - Back in WireShark, filter for only DNS traffic
  - From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com's IP addresses are
  - Observe the DNS traffic being shown in WireShark
</p>
<br />

 <p>
<img src="https://i.imgur.com/c04Sphe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 6: OBSERVE RDP TRAFFIC</h2>

  - In WireShark, filer for RDP traffic only (tcp.port ==3389)
  - Observe the immediate non-stop spam of traffic - because RDP (protocol) is constantly showing you a live stream from one computer to another, therefore traffic is always being transmitted
</p>
<br />
