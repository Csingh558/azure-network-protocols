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

<h2>High-Level Steps</h2>


**Step 1: Create Resources in Azure**
- Create a Resource Group to organize Azure resources effectively.
- Create a Windows 10 VM in the chosen Resource Group, establishing a new Vnet and Subnet.
- Create a Linux (Ubuntu) VM using the same Resource Group and Vnet, and observe the Virtual Network using Network Watcher.

**Step 2: Observe ICMP Traffic**
- Connect to the Windows 10 VM via Remote Desktop and install Wireshark.
- Use Wireshark to observe ICMP traffic:
  - Ping the Ubuntu VM from Windows 10.
  - Perform a perpetual ping.
  - Disable and re-enable ICMP traffic in the Network Security Group.

**Step 3: Observe SSH, DHCP, DNS, and RDP Traffic**
- Continue Wireshark observations for different protocols:
  - Observe SSH traffic by connecting to the Ubuntu VM from Windows 10.
  - Observe DHCP traffic by attempting to renew the IP address of the Windows 10 VM.
  - Observe DNS traffic by querying IP addresses for specific domains.
  - Observe RDP traffic by filtering for RDP-specific traffic (tcp.port == 3389).

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
**Create Resources**

**Step 1: Create a Resource Group**
- Begin by creating a Resource Group to organize your Azure resources efficiently.

**Step 2: Create Windows 10 Virtual Machine (VM)**
- Proceed to create a Windows 10 VM.
- During the VM creation, choose the previously created Resource Group.
- Allow the VM creation to establish a new Virtual Network (Vnet) and Subnet.

**Step 3: Create Linux (Ubuntu) VM**
- Create a Linux (Ubuntu) VM.
- During VM creation, select the previously established Resource Group and Vnet.
- Utilize Network Watcher to observe your Virtual Network.

**Observe ICMP Traffic**

**Step 4: Connect to Windows 10 VM and Install Wireshark**
- Use Remote Desktop to connect to your Windows 10 VM.
- Install Wireshark within the Windows 10 VM.

**Step 5: Observe ICMP Traffic**
- Open Wireshark and filter for ICMP traffic only.
- Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM.
- Observe ping requests and replies within Wireshark.
- From the Windows 10 VM, attempt to ping a public website and observe the traffic in Wireshark.
- Initiate a perpetual ping from Windows 10 VM to Ubuntu VM.
- Disable incoming ICMP traffic in the Network Security Group for the Ubuntu VM.
- Observe ICMP traffic in Wireshark and command line Ping activity.
- Re-enable ICMP traffic and observe the traffic in Wireshark and command line Ping activity (confirm it starts working).
- Stop the ping activity.

**Observe SSH Traffic**

**Step 6: Observe SSH Traffic**
- Filter Wireshark for SSH traffic only.
- SSH into the Ubuntu VM from the Windows 10 VM.
- Type commands into the SSH connection and observe SSH traffic in Wireshark.
- Exit the SSH connection.

**Observe DHCP Traffic**

**Step 7: Observe DHCP Traffic**
- Filter Wireshark for DHCP traffic only.
- Attempt to renew the IP address of the Windows 10 VM using the command line (ipconfig /renew).
- Observe the DHCP traffic in Wireshark.

**Observe DNS Traffic**

**Step 8: Observe DNS Traffic**
- Filter Wireshark for DNS traffic only.
- Use nslookup in the Windows 10 VM's command line to query IP addresses for google.com and disney.com.
- Observe the DNS traffic in Wireshark.

**Observe RDP Traffic**

**Step 9: Observe RDP Traffic**
- Filter Wireshark for RDP traffic only (tcp.port == 3389).
- Note the continuous traffic and consider why it's constant, understanding that RDP provides a live stream from one computer to another.
</p>
<br />


</p>
<br />
