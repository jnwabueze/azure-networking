<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/jIPFIBU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b> Create Resources </b> <br />
- Create a Resource Group. <br />
- Create a Windows 10 Virtual Machine (VM). Allow it to create a new Virtual network (Vnet) and Subnet. <br />
- Create a Linux (Ubuntu) VM. <br />

</p>
<br />

<p>
<img src="https://i.imgur.com/DSdjFEM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b> Observe ICMP Traffic </b> <br />
- Use Remote Desktop to connect to the Windows 10 VM. <br />
- Install Wireshark. <br />
- Open Wireshark and filter for ICMP traffic only. <br />
- Get the private IP address of the Ubuntu VM and attempt to ping it from the Windows VM. <br />
  - Observe ping requests and replies in Wireshark. <br />
- From the Windows VM, in command line or Powershell, attempt to ping a public website and abserve the traffic in Wireshark.<br />
- Initiate a perpetual/non-stop ping from the Windows VM to the Ubuntu VM <br />
  a. Open the Network Security Group your Ubuntu is using and disable inbound ICMP traffic. <br />
  b. In the Windows VM, observe the ICMP traffic in Wireshark and the command line ping activity. <br />
  c. Re-enable ICMP traffic for the Network Security Group the Ubuntu VM is using. <br />
  d. In Windows VM, observe the ICMP traffic in Wireshark and the command line ping activity (should start working again!). <br />
  e. Terminate the ping activity.

</p>
<br />

<p>
<img src="https://i.imgur.com/lspVesb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<b> Observe SSh Traffic </b><br />
- Back in Wireshark, filter for SSH traffic only. <br />
- From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address). <br />
a.	Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark. <br />
b.	Exit the SSH connection by typing ‘exit’ and pressing [Enter]. <br />

<b> Observe DHCP Traffic </b> <br />
- Back in Wireshark, filter for DHCP traffic only. <br />
- From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew). <br />
a.	Observe the DHCP traffic appearing in WireShark. <br />

<b> Observe DNS Traffic </b> <br />
- Back in Wireshark, filter for DNS traffic only. <br />
- From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are. <br />
a.	Observe the DNS traffic being show in WireShark. <br />

<b> Observe RDP Traffic </b> <br />
- In Wireshark, filter for RDP traffic only (tcp.port == 3389). <br />
</p>
<br />
