<h1>Virtual Private Network (VPN)</h1>

<p align="center">
  <img src="https://i.imgur.com/MntON5Q.png" height="80%" width="80%" alt="VPN Diagram"/>
</p>

<h1>Setting Up a VPN and Verifying Location with Azure</h1>
<p>This guide walks you through setting up a VPN connection using a virtual machine hosted on Azure, and viewing location/IP changes throughout the process.</p>

<h2>Tools and Platforms Used</h2>

<ul>
  <li>Proton VPN (Free VPN Service)</li>
  <li>Microsoft Azure (VM Deployment)</li>
  <li>Remote Desktop</li>
  <li>Internet Information Services (IIS)</li>
</ul>

<h2>Operating System</h2>
<ul>
  <li>Windows 10 (21H2)</li>
</ul>

<h2>Process Outline</h2>

<ul>
  <li>Step 1 – Check Local IP</li>
  <li>Step 2 – Create a Virtual Machine on Azure</li>
  <li>Step 3 – Confirm VM IP (France Location)</li>
  <li>Step 4 – Install and Connect to VPN from VM</li>
  <li>Step 5 – Confirm New VPN IP (Japan Location)</li>
</ul>

<h2>Instructions</h2>

<h3>Step 1 – Identify Your Personal IP</h3>
<p>Visit <a href="https://www.whatismyipaddress.com" target="_blank">whatismyipaddress.com</a> to view your home network's public IP. Make note of this for later comparison.</p>
<p><img src="https://i.imgur.com/qDgu5K6.png" height="80%" width="80%" alt="Local IP Check"/></p>

<h3>Step 2 – Deploying an Azure VM</h3>
<p>Head to <a href="https://portal.azure.com" target="_blank">portal.azure.com</a> and navigate to the Virtual Machines section. If needed, create a free Azure account with credits. Refer to the example setup screen below.</p>
<p><img src="https://i.imgur.com/K9oaS2z.png" height="80%" width="80%" alt="Azure VM Setup"/></p>

<p>Name your VM something like “VM-FranceCentral” and choose the same region (France Central). Follow the configuration shown in the examples.</p>
<p><img src="https://i.imgur.com/u3vclL3.png" height="80%" width="80%" alt="VM Naming"/></p>

<p>Set up a custom admin username and password you’ll remember.</p>
<p><img src="https://github.com/user-attachments/assets/873cfc08-1e7e-4b55-8b54-164609095966" height="80%" width="80%" alt="Admin Config"/></p>

<p>Move to the Networking tab and replicate the input options from the next image.</p>
<p><img src="https://github.com/user-attachments/assets/9e9c69eb-47f1-41c9-85e3-ef1523509d88" height="80%" width="80%" alt="Networking Settings"/></p>

<p>Click “Review + Create.” After validation completes, select “Create.” Once deployed, note the public IP address of the VM (e.g., 20.216.176.18).</p>
<p><img src="https://i.imgur.com/ZlH9zI5.png" height="80%" width="80%" alt="VM IP Address"/></p>

<h3>Step 3 – Connect to VM and Verify Location</h3>
<p>Use Remote Desktop Connection from your PC and connect to the VM using the IP address and login credentials.</p>
<p><img src="https://i.imgur.com/YPBkMau.png" height="80%" width="80%" alt="RDP App"/></p>
<p><img src="https://github.com/user-attachments/assets/d4a6fe23-57ad-4168-8c3b-86f7214853e7" height="80%" width="80%" alt="RDP Login"/></p>

<p>Inside the VM, open a browser and revisit whatismyipaddress.com. The result should reflect a France-based IP.</p>
<p><img src="https://i.imgur.com/nWlX2UM.png" height="80%" width="80%" alt="France IP"/></p>

<h3>Step 4 – VPN Setup Within VM</h3>
<p>On your personal computer, go to <a href="https://protonvpn.com" target="_blank">protonvpn.com</a> and create a free account. Once created, copy the login URL and paste it into the browser inside the VM.</p>
<p><img src="https://github.com/user-attachments/assets/413889e6-6875-4ad9-b707-89c043fdf854" height="80%" width="80%" alt="ProtonVPN"/></p>

<p>Log in to Proton VPN on the VM and download the Windows app. After installation, sign in and connect to a VPN server (e.g., Japan). You should see something like this:</p>
<p><img src="https://i.imgur.com/oqPHozb.png" height="80%" width="80%" alt="Connected VPN"/></p>

<p>Select a location like Japan on the left-hand side, then confirm your VPN is active with the new connection.</p>
<p><img src="https://i.imgur.com/6Rdgg6B.png" height="80%" width="80%" alt="Japan VPN IP"/></p>

<h3>Step 5 – Confirm New VPN IP</h3>
<p>While still in the VM, revisit whatismyipaddress.com again. You’ll now see a Japanese IP, showing that the VPN is successfully tunneling traffic from a different region.</p>
<p><img src="https://i.imgur.com/lQsISWb.png" height="80%" width="80%" alt="VPN Japan IP"/></p>

<h3>Summary</h3>
<p>Throughout this exercise, you successfully used 3 distinct IP addresses:</p>
<ul>
  <li>Home IP (USA): 137.103.51.136</li>
  <li>VM IP (France): 20.216.176.18</li>
  <li>VPN IP (Japan): 212.102.51.251</li>
</ul>

<p>Before finishing, remember to clean up your Azure resources to avoid unexpected charges. You can delete the resource group to remove the VM completely.</p>

