<h1>Microsoft Azure - Virtual Machines, Network Security Groups & Packet Analysis</h1>

<h2>Description</h2>
This repository documents the setup and configuration of **Microsoft Azure Virtual Machines (VMs)**, **Network Security Groups (NSGs)**, and the monitoring of network traffic using **Wireshark**. The project demonstrates how to deploy a cloud-based infrastructure with secure network policies and packet-level analysis to enhance security and performance tracking.  
<br />

<h2>Key Features & Configurations</h2>

- <b>Virtual Machine Deployment:</b> Configured Windows and Linux-based VMs in Azure.
- <b>Network Security Groups (NSGs):</b> Implemented inbound/outbound rules for controlled access.
- <b>Remote Access Configuration:</b> Configured SSH & RDP access for secure remote management.
- <b>Firewall & Port Restrictions:</b> Enforced security policies using Azure Firewall & NSG rules.
- <b>Packet Capture & Network Monitoring:</b> Used **Wireshark** to analyze network traffic.
- <b>Logging & Analytics:</b> Enabled Azure Network Watcher to track security and connectivity insights.

<h2>Environments Used</h2>

- <b>Microsoft Azure Portal</b> (Cloud Infrastructure)
- <b>Windows Server 2022</b> (Deployed VM)
- <b>Ubuntu 20.04 LTS</b> (Linux-based VM)
- <b>Wireshark</b> (Network Packet Analyzer)

<h2>Project Walkthrough:</h2>

<p align="center">
Creating a Virtual Machine in Azure: <br/>
<img src="https://imgur.com/ckUj7LJ.png" height="80%" width="80%" alt="Azure VM Deployment"/>
<img src="https://imgur.com/pvjGl9G.png" height="80%" width="80%" alt="Azure VM Deployment"/>
<br />
Creating a Resource Group in Azure: <br/>
<img src="https://imgur.com/wb6YuaA.png" height="80%" width="80%" alt="Azure VM Deployment"/>
<br />
Configuring Network Security Groups (NSGs):  <br/>
<img src="https://imgur.com/3Ze8Dbx.png" height="80%" width="80%" alt="NSG Configuration"/>
<br />

<h2>Step-by-Step Deployment Guide</h2>

<h3>1. Setting Up a Virtual Machine</h3>
<ul>
    <li>Log into <b>Azure Portal</b> and navigate to **Virtual Machines**.</li>
    <li>Click **Create VM**, select **Windows Server 2022** or **Ubuntu 20.04**.</li>
    <li>Choose an appropriate **VM size**, resource group, and region.</li>
    <li>Set up **Administrator Credentials** for RDP or SSH access.</li>
    <li>Enable **Public IP Address** (if required) for external access.</li>
</ul>

<h3>2. Configuring Network Security Groups (NSGs)</h3>
<ul>
    <li>Navigate to **Networking** section in the VM settings.</li>
    <li>Create a **Network Security Group (NSG)**.</li>
    <li>Define **Inbound & Outbound Rules** for port restrictions.</li>
    <li>Allow only necessary ports (e.g., **RDP - 3389, SSH - 22**).</li>
    <li>Restrict all other unauthorized connections.</li>
</ul>

<h3>3. Remote Access & Firewall Configuration</h3>
<ul>
    <li>For <b>Windows VM</b>, use **RDP** to connect (Remote Desktop Connection).</li>
    <li>For <b>Linux VM</b>, use **SSH** via Terminal or PuTTY.</li>
    <li>Ensure firewall rules align with NSG configurations.</li>
</ul>

<h3>4. Packet Capture & Network Traffic Analysis (Wireshark)</h3>
<ul>
    <li>Install **Wireshark** on the VM.</li>
    <li>Start a **Live Capture** session on the network interface.</li>
    <li>Analyze incoming/outgoing packets for suspicious activity.</li>
    <li>Filter by IP addresses, ports, and protocols (e.g., **TCP, UDP, ICMP**).</li>
</ul>

<h3>5. Monitoring Logs & Alerts in Azure</h3>
<ul>
    <li>Enable **Azure Network Watcher** for real-time logging.</li>
    <li>Set up **log analytics** to track VM activity.</li>
    <li>Define alerts for **unauthorized access attempts**.</li>
</ul>

<h2>How to Deploy This Project</h2>
<ol>
    <li>Set up an <b>Azure Subscription</b> and access the **Azure Portal**.</li>
    <li>Deploy a **Windows/Linux Virtual Machine**.</li>
    <li>Configure **Network Security Groups (NSGs)** and enforce firewall policies.</li>
    <li>Set up **Remote Access (RDP/SSH)** with secure credentials.</li>
    <li>Install **Wireshark** and monitor real-time network packets.</li>
    <li>Enable **Azure Monitor & Network Watcher** for security insights.</li>
</ol>

<h2>Conclusion</h2>
This project demonstrates the **deployment and security hardening** of Azure Virtual Machines using **Network Security Groups (NSGs)** and **Wireshark-based network traffic analysis**. The implementation ensures **secure remote access, controlled network traffic, and proactive monitoring of system activity** to mitigate potential threats.

<!--
```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
