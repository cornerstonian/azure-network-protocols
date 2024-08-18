<p align="center">
<img src="https://imgur.com/svYdA1p.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
Outline for examining network traffic between Azure Virtual Machines using Wireshark. It includes creating and configuring VMs, observing various network protocols (ICMP, SSH, DHCP, DNS, RDP) and experimenting with Network Security Groups to manage and secure traffic. This project includes hands-on experience in network traffic analysis and the practical application of network security concepts within Azure environments. <br />

<h2>What is Wireshark</h2>
Wireshark is a popular open-source network protocol analyzer used for network troubleshooting, analysis, and education. It allows users to capture and examine the data traveling across a network in real time. Wireshark is widely used by network administrators, security professionals, and developers to troubleshoot network issues, optimize performance, and ensure security. Its comprehensive analysis capabilities make it an essential tool for anyone involved in managing or developing networked systems.

Key features:

1. **Packet Capture**: Captures packets of data that flow through a network interface, recording detailed information about each packet, such as source and destination IP addresses, protocols used, and payload data.
2. **Protocol Analysis**: Decodes and displays the information in a human-readable format, supporting a wide range of network protocols. 
3. **Filtering and Searching**: Users can apply filters to focus on specific types of traffic or specific conversations, making it easier to identify and analyze relevant data amidst potentially large volumes of network traffic.
4. **Visualization**: Provides various visualization tools, including graphs and statistics, which can help in diagnosing network issues and understanding traffic patterns.
5. **Cross-Platform**: Available on multiple operating systems, including Windows, macOS, and Linux, making it versatile for different environments.
6. **Export and Reporting**: Captured data can be exported in various formats for further analysis or reporting, facilitating detailed examination and documentation.

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

- Create VMs and Install Wireshark
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic (Bonus)

<h2>Actions and Observations</h2>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


Part 1 (Create our Resources)
- Create a Resource Group
- Create a Windows 10 Virtual Machine (VM)
- While creating the VM, select the previously created Resource Group
- While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
- Create a Linux (Ubuntu) VM
- While create the VM, select the previously created Resource Group and Vnet
- Observe Your Virtual Network within Network Watcher

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Part 2 (Observe ICMP Traffic)
- Use Remote Desktop to connect to your Windows 10 Virtual Machine
- Within your Windows 10 Virtual Machine, Install Wireshark
- Open Wireshark and filter for ICMP traffic only
- Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
- Observe ping requests and replies within WireShark
- From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
- Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
- Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
- Stop the ping activity

Part 3 (Observe SSH Traffic)
- Back in Wireshark, filter for SSH traffic only
- From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
- Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
- Exit the SSH connection by typing ‘exit’ and pressing [Enter]
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Part 4 (Observe DHCP Traffic)
- Back in Wireshark, filter for DHCP traffic only
- From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
- Observe the DHCP traffic appearing in WireShark

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Part 5 (Observe DNS Traffic)
- Back in Wireshark, filter for DNS traffic only
- From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
- Observe the DNS traffic being show in WireShark
  
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Part 6 (Observe RDP Traffic)
- Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)
- <b>Bonus!</b> Observe the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?

<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

- Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted

<h2 align="center"> Various forms of network traffic have been observed with Wireshark as well as some basics with Network Security Groups </h2>

