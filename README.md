# Ancora-Education-Ucertify-Lab15
# Creating a DMZ Zone

A demilitarized zone (DMZ) is a physical or logical subnetwork that contains and exposes an organization's external-facing services to an untrusted, usually larger, network. DMZs allow organizations to isolate their internal networks from external networks, such as the Internet, while still providing access to services that must be accessible from the Internet.

> **Original Lab Source**

> This lab was available through:
[https://ancoraeducation.ucertify.com/app/func=navigate_items&item_sequence=6]

## Software Used 
The PuTTY SSH Client is used in this lab. It is a popular SSH and Telnet Client that provides a secure way to access remote systems.

## Lab/Machine Environment
You are provided with the Linux virtual machine.

# Objective of the Lab
This lab session demonstrates the steps involved in creating a demilitarized zone. Upon completion of this lab, you will be able to: 

Understand the concept of DMZ and its importance in network security. 

Configure a DMZ to provide secure access to internal services. 

Define a DMZ with appropriate IP address ranges, subnet masks, and other options.

## Topology Used
Topology refers to the arrangement or configuration of the virtual network connections within the virtual machine (VM) environment. It defines how the virtual network interfaces and components are interconnected and organized.

## PART A: Accessing PC3 Terminal and Pinging the Host
Access the PuTTY console with IP address as 192.168.116.128, Port as 5011, and Connection type as Other. In the PC3 terminal, execute the command to ping the 192.168.1.100 host.
### STEP 1
From the left sidebar, open PuTTY SSH Client. The PuTTY Configuration window will appear on the screen.

### STEP 2
Type Host Name (or IP address) as 192.168.116.128.

### STEP 3
Type Port as 5011.

### STEP 4
Select the Other radio button.

### STEP 5
Click Open to connect to the PC3 terminal window.

### STEP 6
If you don't get a command line prompt in the terminal window, then press Enter.

### STEP 7
Execute the following command to ping the 192.168.1.100 host:
```bash
ping 192.168.1.100
```
**CAUTION**

If the ping does not work immediately, wait a few seconds and try again.

### STEP 8
You will observe that PC3 is able to ping the 192.168.1.100 host.

### STEP 9
Minimize the PC3 terminal window.

## PART B: Accessing the R9 Terminal and Configuring Router Settings
Access the PuTTY console with IP address as 192.168.116.128, Port as 5004, and Connection type as Other. In the R9 terminal, execute the commands to enter into configuration mode and deny IP traffic from the source IP address range 192.168.2.101 to the destination IP address range 192.168.1.0 on interface e0/1.

### STEP 1
From the left sidebar, right-click the PuTTY SSH Client () icon, and from the list that appears, select New Window.

### STEP 2
Type Host Name (or IP address) as 192.168.116.128

### STEP 3
Type Port as 5004.

### STEP 4
Select the Other radio button.

### STEP 5
Click Open to connect the router R9 terminal window.

### STEP 6
If you don't get a command line prompt in the terminal window, then press Enter.

### STEP 7
Execute the following command to enter into configuration mode:
```bash
conf t
```

### STEP 8
Execute the following commands to create the access list and deny the host. (Note: Execute one command at a time.):
```bash
access-list 100 deny ip 192.168.2.101 0.0.0.255 192.168.1.0 0.0.0.255
```
```bash
access-list 100 permit ip any any
```
```bash
interface e0/1
```
```bash
IP access-group 100 in
```
```bash
end
```
### Note
The access-list 100 deny ip 192.168.2.101 0.0.0.255 192.168.1.0 0.0.0.255 command is used to deny IP traffic from the source IP address range 192.168.2.101 to the destination IP address range 192.168.1.0. 

The access-list 100 permit ip any any command allows all IP traffic from any source IP address to any destination IP address. 

The interface e0/1 command is used to access or configure the Ethernet interface e0/1. 

The IP access-group 100 in command is used to apply an ACL with the number 100 to the inbound traffic on an interface.

### STEP 9
Execute the following command to save router settings:
```bash
copy running-config startup-config
```
### Note
The copy running-config startup-config command is used to save the current running configuration of a network device, such as a router or switch, to the startup configuration file.

### STEEP 10
When asked Destination filename [startup-config]?, press Enter.

### STEP 11
Execute the following command to check the access list:
```bash
show access-lists
```
### STEP 12
Close the R9 terminal window. At the PuTTY Exit Confirmation prompt, click Yes.

## PART C: Verifying the Router Settings and Pinging the Host
Execute the command to ping the 192.168.1.100 host and verify the ping result

### STEP 1
On the left sidebar, click the PuTTY SSH Client icon and restore the PC3 terminal window.

### STEP 2
Execute the following command to ping the 192.168.1.100 host:
```bash
ping 192.168.1.100
```

### STEP 3
You will observe that PC3 is not able to ping the 192.168.1.100 host and Communication administratively prohibited message is displayed.

### STEP 4
Close all windows. At the PuTTY Exit Confirmation prompt, click Yes

## LAB SUMMARY
This lab session provides you with a straightforward and practical understanding of DMZs and how to create a DMZ. Here's a summary of what you have learned:

How to configure a DMZ to provide secure access to internal services. 

How to define a DMZ with appropriate IP address ranges, subnet masks, and other options. 

Now, you are equipped with the knowledge and skills to set up a DMZ effectively, secure access to internal services, and enhance the security of your network infrastructure.

## Disclaimer

This repository is for **educational and personal learning purposes only**.  

The original lab content belongs to **uCertify / Ancora Education** and remains their copyrighted material.  
This repository is not affiliated with, endorsed by, or sponsored by uCertify or Ancora Education.  

No copyright infringement is intended.  
Use of any tools or techniques mentioned here should only be performed in authorized, legal environments.
