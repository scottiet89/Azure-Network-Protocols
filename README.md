# Azure-Network-Protocols
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we will observe various network traffic protocols to and from Azure Virtual Machines with Wireshark, and we will also experiment with Network Security Groups. <br />

<h2>Video Demonstration</h2>

- ### [YouTube: Lab Tutorial: Inspecting Traffic And Network Security Groups (NSGs) With Microsoft Azure VMs](https://youtu.be/xpSPjCKVdW8)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Deployment and Configuration Steps</h2>

<p>Section 1: Click “Resource groups” in Microsoft Azure -> Click “Create resource group” -> After typing the resource groups name click “Review + create” -> Type or select “Virtual Machines” -> Select the create button and then click “Azure virtual machine” -> Select the resource group you just created previously -> Type “VM1” as the virtual machine name -> Select “Windows 10” as the image -> Enter and note down a username and password (It’s a must to remember it) -> Check the licensing checkbox then select “Review + create” (leave every option default) -> Create another VM in the same fashion, the only things that are going to be different is you must use the name VM2 and select “Ubuntu” as the image  -> Type and select “Network Watcher” in Azure -> Click “Topology” under “Monitoring” -> Select the resource group you previously created and the VM1-vnet option (This shows the layout of the virtual network we are going to be inspecting)</p>
<img src="https://i.gyazo.com/a23d69f7a387af8a49415d0d045e52ee.png">
<img src="https://i.gyazo.com/9d90d8f07497cd25bcc57b9c008e38e0.png">
<img src="https://i.gyazo.com/c8531d3d56e574c09d7327b300c2f918.png">
<img src="https://i.gyazo.com/790599f70a7cf08a963383ec66d488f0.png">
<img src="https://i.gyazo.com/a3ca2866453fd1bf678ed0d4e274f93b.png">
<img src="https://i.gyazo.com/97e4b14f38116fe573bfd57a607425c5.png">
<img src="https://i.gyazo.com/36cc111132c14573eb0cdf4e7c73c930.png">
<img src="https://i.gyazo.com/09f4ee42ebb0aedb731bb8143dd744a4.png">
<img src="https://i.gyazo.com/4ca52fc69563efe897ded83f52837391.png">
<img src="https://i.gyazo.com/17d16485e7416cdb84628afbffe7bacf.png">
<img src="https://i.gyazo.com/2aab57df50b46f8ca04c9071a2db584f.png">
<img src="https://i.gyazo.com/260bcd1c9f157b1afeeb5c312d10a206.png">
<img src="https://i.gyazo.com/12d30aacbf1c43922bf1e012dcdb908a.png">
<img src="https://i.gyazo.com/8790ebfc63b47b1dd5c55dff17ef4166.png">
<img src="https://i.gyazo.com/bb2edcbba4a5c2adaecccd6d05622b46.png">
<img src="https://i.gyazo.com/e47caa07d9edd89ab81d698bb1354a57.png">
<img src="https://i.gyazo.com/fa67460f0941c9f494709f789e0f541d.png">
<img src="https://i.gyazo.com/c500a7c4a79a18f9c2611527ffde4d50.png">
<p>Now we are going to enter into VM1 via the use of the windows software application "remote desktop connection", then we are gonna install Wireshark to inspect the internet traffic of VM1 and VM2.

Section 2: Head to “Virtual machines” in Azure -> Click “VM1” -> Copy the “Public IP address” -> Open the software “Remote Desktop Connection” on your personal PC -> Paste VM1’s public IP address -> Connect and login using the credentials you gave VM1 -> Open Microsoft Edge and search “wireshark download” then select the first link -> Download the windows installer option -> Open the installation .exe and install it and be sure to leave every option at default -> Once it’s done being installed open “Wireshark” -> Double click “Ethernet” -> Type and then enter “icmp” to filter the traffic type “ICMP” -> Copy the private ip address of VM2 in Azure -> Open command prompt and type and enter “ping <VM2 private ip address> (Note: Refer to this steps screenshot below) -> Observe the ping request and replies in Wireshark -> Type and enter <ping www.google.com> into command prompt then observe Wireshark -> Type and enter <ping -t <VM2 private ip address> (This will continuously ping VM2 until we tell it to stop) -> In Microsoft Azure within VM2 select “Networking” under “Settings” -> Click “Add inbound port rule” -> Select Protocol: ICMP and Action: Deny then click “Add” (This will disable any incoming inbound ICMP traffic) -> Observe that the pings are now changed to “Request timed out” -> Enter into the options of the rule that you just created in Azure -> Select Action: Allow and click “Save” (This will now enable any incoming inbound ICMP traffic) -> Observe Wireshark and then stop the ping in command prompt by pressing “Ctrl + c” on your keyboard
</p>
<img src="https://i.gyazo.com/07d7813764d989411a12ddef9f4c0930.png">
<img src="https://i.gyazo.com/cce9d430a6f1575ab1f753baa038f146.png">
<img src="https://i.gyazo.com/cf1d377fb9fc14698005f1c12e562b52.png">
<img src="https://i.gyazo.com/398b6cd9a981a58b3c1de0135ac6f01a.png">
<img src="https://i.gyazo.com/0ec3cbca56e461850c6711296fa99027.png">
<img src="https://i.gyazo.com/1cbef3b8d56b3f1b9374f66340786021.png">
<img src="https://i.gyazo.com/ecd1497d1eb775a3f487c4d95918304e.png">
<img src="https://i.gyazo.com/0e33a70b7077e9497de6680ebbb4b76a.png">
<img src="https://i.gyazo.com/78a6ab7afa9ff6213dbc800f13c10b23.png">
<img src="https://i.gyazo.com/c16ae51f6615cd5e7b2cac70e20addb7.png">
<img src="https://i.gyazo.com/6f621e6338bc1fbec833df0f5e590f5c.png">
<img src="https://i.gyazo.com/a4097f547c87c3204d01f595c3630c34.png">
<img src="https://i.gyazo.com/6248f284f0fe490a2baf4b833ffea4f0.png">
<img src="https://i.gyazo.com/4190e12a2ab51a6c18bd63820678a610.png">
<img src="https://i.gyazo.com/cce76a103a9f2a77474ea8200b0276b1.png">
<img src="https://i.gyazo.com/ae998354f600cbb1b8117aa428081796.png">
<img src="https://i.gyazo.com/d37131248fd1d6b2aa8252be7344d759.png">
<img src="https://i.gyazo.com/d8f4dd44d1ffbb0f45ddd75e9a42c245.png">
<img src="https://i.gyazo.com/0d62009bbaf512b4c701a34b9b498855.png">
<img src="https://i.gyazo.com/ebac074628b9b76a5d1b5ed332f5c61a.png">
<img src="https://i.gyazo.com/9125118653bdc91f52c3302b967d4f93.png">
<img src="https://i.gyazo.com/852f334ba783d73bf4dc43cd06df565e.png">
<img src="https://i.gyazo.com/f9cedc7fc40ff4d114cf559ed753dfdc.png">
<p>Section 3: In wireshark type and enter “ssh” -> In command prompt type and enter ssh and then VM2’s private ip address (example: ssh 10.0.0.5) -> Type and enter “yes” -> Enter in VM2’s password (Note: You won’t be able to see the text you’re typing but type it normally then press enter as usual) -> Observe what’s popped up in Wireshark then enter the commands username, pwd, and lastly the command exit</p>
<img src="https://i.gyazo.com/f5c573528ef737485a7de5bd28ad87c6.png">
<img src="https://i.gyazo.com/09cfede832acc205b4c95bd59a9d0420.png">
<img src="https://i.gyazo.com/f11ebad8280d57df71954ef39999d338.png">
<img src="https://i.gyazo.com/6e652ded68acc71e453a69926d0fa284.png">
<img src="https://i.gyazo.com/c833ccc66c5e374f88e3e8f76bc496b2.png">
<p>Section 4: In wireshark type and enter “dhcp” -> Type ipconfig /renew into command prompt -> Observe the changes in Wireshark</p>
<img src="https://i.gyazo.com/284c7fe6a0ff49fa04316386c434c1ee.png">
<img src="https://i.gyazo.com/603ceabfab73726124788941f9bbff17.png">
<p>Section 5: In wireshark type and enter “dns” -> Type nslookup www.google.com into command prompt -> Then type nslookup www.disney.com -> Observe the changes in Wireshark</p>
<img src="https://i.gyazo.com/ed8cc3002335d6a0f49a77ee4f81c9e5.png">
<img src="https://i.gyazo.com/709a9ad5b3eceab70bb8c6a3904ca82d.png">
<img src="https://i.gyazo.com/48cd847e068069fa5e588a08ee4567a5.png">
<p>Section 6: In wireshark type and enter “tcp.port == 3389” (Note: The traffic will be nonstop bpdating in Wireshark, the reason for this is that “tcp.port == 3389” traffics only remote desktop protocols.)</p>
<img src="https://i.gyazo.com/7cf25e30ca43cd83d47a43e69e6a0635.png">
<p>Congrats you’ve just completed all of the steps for this network traffic protocol tutorial!</p>
