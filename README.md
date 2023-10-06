<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (RDP, ICMP, SSH, DNS)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Captured packets for a variety of network traffic with Wireshark
- Allowed inbound ICMP
- Remoted to Ubuntu with SSH and navigated terminal capturing SSH traffic in Wireshark
- Observed DNS packets with nslookup

<h2>Actions and Observations</h2>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/f2be1ab6-1a60-449a-a701-f39db4a60f70" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/c160418a-93d8-4623-8a11-52ef81b47b65" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created an inbound rule in Azure to deny all ICMP traffic and edited the rule to allow ICMP traffic. I used Windows Remote Desktop to interact with my Windows VW and from there I pinged my Ubuntu VM with "-t" so it would continually send packets. I used Wireshark to capture the ICMP requests and observed the replies from my Ubuntu VM as the rule change took effect.   
</p>
<br />

<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/01dc3c5a-b791-472d-b223-898aede5946e"/>
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/e3c7a882-d440-4bd5-8c08-b7a733e65168" />
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/d9180919-39e8-48a1-abc1-45f22d1679ec"/>
</p>
<p>
Used SSH protocol to connect to and navigate in Ubunutu VM and used Wireshark to observe the packets.
</p>
<br />

<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/4eabaa91-96be-44d8-a38d-042888ebea38"/>
</p>
<p>
  Captured and observed DNS traffic with nslookup. 
</p>
