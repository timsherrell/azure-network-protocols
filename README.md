<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (RDP, ICMP, SSH)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Observed traffic with Wireshark
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/f2be1ab6-1a60-449a-a701-f39db4a60f70" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/c160418a-93d8-4623-8a11-52ef81b47b65" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I created an inbound rule in Azure to deny all ICMP traffic and edited the rule to allow ICMP traffic. I used Windows Remote Desktop to interact with my Windows VW and from there I pinged my Ubuntu VM with "-t" so it would continually send packets. I used Wireshark to capture the ICMP requests and observed the replies from my Ubuntu VM as the rule change took effect.   
</p>
<br />

<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/01dc3c5a-b791-472d-b223-898aede5946e"/>
</p>

<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/d9180919-39e8-48a1-abc1-45f22d1679ec"/>
</p>
<p>
I used SSH protocol to connect to my Ubunutu VM and used Wireshark to anaylze the packets.
</p>
<br />
