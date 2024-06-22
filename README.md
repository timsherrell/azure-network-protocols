<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. This tutorial assumes you have already created your virtual machines in Azure. <br />

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
  We can go to portal.azure.com and find our Windows 10 VM (virtual machine). If it isn't on the first page we can use the search bar to look for either virtual machines for our Windows VM or resource groups for the resource group we created for our virtual machines. 
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/f0304c56-1d72-4d18-8a08-3c1fbcac8962" />
</p>
<p>
  We will click on the resource group we created to store our VMs. 
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/469e2150-626c-43c3-9ab0-39496e642841" />
</p>
<p>
  We copy the public IP address of our Windows 10 machine and paste it into Windows Remote Desktop Connection. 
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/913588f4-4426-40f8-8a4e-e1e0682e52ff" />
</p>
<p>
  Paste the IP into the Remote Connection window. 
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/91464230-49c0-4d4f-af67-1e22d0803dca" />
</p>
<p>
  Click more choices to sign in with the credentials we created in Azure when you created our Windows 10 virtual machine.
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/57c535cd-7487-4a50-a94d-c3b389569b95" />
</p>
<p>
  Go ahead and click past the warning about certificate errors. We can safely ignore this. 
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/abc256c6-e7ab-492a-a01d-9ee8a091518f" />
</p>
<br />

<p>
  While the OS loads we can take a look at the firewall in Azure and set a rule to help us understand the flow of network traffic. We will capture and observe the traffic with Wireshark a little down the road. For now let's go back to our resource group on Azure.    
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/0f5fa600-6977-480a-8ae0-e9feac6b3509" />
</p>
<p>
  We want to find our Windows VM network security group (WindowsVM-nsg). 
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/21409353-eeff-4c60-af89-f3dbcaa50ba4" />
</p>
<p>
  We can find Inbound Security Rules in the side panel. This will allow us to create an inbound rule for a specific port. We click on Inbound security rules and click "Add New."
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/93c163d2-963a-474f-835a-252ad52b2109" />
</p>
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/ea9db12b-f971-47eb-818d-7c7d79aefaeb" />
</p>
Select ICMP. There is no need to specify a port here. In the name field, we type something that describes our purpose in creating the rule. We will deny ICMP to view how the ping command behaves when ICMP is denied and then allow ICMP traffic to see the difference.  
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/926f2673-8925-4d62-a568-6482bd35eee6" />
</p>
Bring up Wireshark and filter for ICMP. 
<p>
  <img src="https://github.com/timsherrell/azure-network-protocols/assets/144177449/c160418a-93d8-4623-8a11-52ef81b47b65" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Created an inbound rule in Azure to deny all ICMP traffic and edited the rule to allow ICMP traffic. We used Windows Remote Desktop to interact with my Windows VW and from there we pinged my Ubuntu VM with "-t" so it would continually send packets. We used Wireshark to capture the ICMP requests and observed the replies from my Ubuntu VM as the rule change took effect.   
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
