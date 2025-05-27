# network_subnetting

First of all, all the information here is taken from the NetPractice project of 1337/42 school, and the purpose is just to simplify the project for others and refresh the project concepts for better understanding.

## What you will learn here:
- What is an IP?
- What is a MAC?
- What is a router?
- What is a switch?
- What is subnetting?
- What are the types of networks?
- And a lot of things to check out for yourself.

---

## What is an IP address?

**IP** stands for **Internet Protocol**, which means it is an internet address. Without it, we cannot access the internet.

We have two different types of IPs: **IPv4** and **IPv6**.  
Here we will talk about **IPv4**, as it is most used nowadays.

IPv4 also has two types: **private IP** and **public IP** addresses. Let's talk briefly about the purpose of each one:

- The **private IP address** is a unique address in the LAN (Local Area Network), and with it, we can access all the devices in the LAN.  
- As I said, it’s just for the LAN — meaning we cannot use it to access the internet.

- The **public IP address** is unique in the public network, which means no one has your public IP address in the public network. This IP is provided by the ISP(Internet Service Provider)
Like here in Morocco, we have "Maroc Telecom" as an ISP, for example, that provides you with an IP address, but the question is, what makes it unique? Is it not duplicated?
the answer of the qusiton is the IANA(Internet Assigned Numbers Authority), manages three critical internet components: IP addressing, DNS root zone management, and protocol parameters, serving as the global coordinator for these essential resources. While operating under ICANN's structure, IANA maintains operational independence in managing internet's core numbering systems.
- We can say that the IANA gives a pool of IPs to the ISPs, who then divide them and assign them to users of the internet. We pay for the IP address that gives us the ability to access the internet.

**Bonus:** IP addresses have 5 classes you need to know.  
You have a range of classes you can use based on the number of LAN devices. If you have more than 256 devices, you will not use **Class C**.

---

## The 5 Classes:

- **Class A** → `10.0.0.0/8`
- **Class B** → `172.0.0.0/16`
- **Class C** → `192.168.0.0/24` → This is the most famous one used in a home LAN.
- **Class D** → NOT USED (reserved)
- **Class E** → NOT USED (reserved)

---

Picture from -> https://www.tecmint.com/network-ip-addressing-range/  
![Classes-of-IP-Addresses](https://github.com/user-attachments/assets/b36c02bc-eb69-496b-8957-0dc743153f26)


- **Class A** gives us a range of `2^24` (24 bits free), which is 16,777,216 addresses — a huge number for a HOME LAN. That’s why it’s not popular there.
- **Class B** gives `2^16 = 65,536` IPs — good for a medium-sized LAN.
- **Class C** gives `2^8 = 256` devices in the LAN network, which is perfect for a small home network.

---

## Let's talk about the **gateway** and the **broadcast** of an IP address (IPv4):

You might ask: Why not 255 and 256?  
Here’s the idea: the first address (ending in `.0`) is the **network address**, and the last one (ending in `.255`) is the **broadcast address**.  
These two are **not used for devices**, which leaves you with 254 usable addresses in a `/24` range.

---

### What is the broadcast?

Imagine we have a protocol like **ARP** (you can learn about this protocol if you're interested).  
Every time ARP wants to get the MAC address of another device, it only knows that device's IP address.  

Since it doesn’t know the exact path or location of that device, it uses the **broadcast address** (the last IP in the subnet) to send the request to **everyone** in the network, asking who has that IP address.

You cannot assign a broadcast IP to a device — it’s only used for communication with **all** devices.

---

## What is the network address and the gateway?

Let’s talk first about the **network address**.

Imagine we have a lot of networks. Before specifying the IP address of a destination device, we must know the network address of that destination — because within a larger network, there can be many smaller subnetworks.

> (To better understand this, look at the picture below.)

---

Picture from → https://mockflow.com/flowchart-examples/cisco-network-diagram-example-network-address-translation
<img width="1729" alt="shapes at 25-05-27 10 42 26" src="https://github.com/user-attachments/assets/9ed73955-efe0-4fc2-a75e-d5026a613f8f" />
 
- **The network address** – to know which network the destination is part of.  
- **The host (device) address** – to know which device inside that network you want to reach.  

In IPv4, this is handled by dividing the IP address into:  
- **Network part** (based on the subnet mask, like `/24`)  
- **Host part** (specific to the device)  

Let’s talk first about the **gateway address**.
As your device has an IP address, the router(we will talk about it later on) has an IP, and if we talking about the IP address, we will use the public one to get the internet


Example:
If the IP is 192.168.1.42/24:  
    Network address = 192.168.1.0  
    Host address = 42 (the unique ID of the device in that network)  

In summary, the Gateway IP address should not be assigned to any device within the local area network (LAN), because it is reserved for the router or gateway itself. The gateway serves as the only path through which devices in the LAN can access external networks, such as the Internet.
NOTE: In the LAN every one have a unique privet IP address rather than the public IP in the LAN, we just have one.  
But how do all the users in the LAN use just one **public IP address**
If you think about it, we are 8 billion in the world, and the number of IPs possible to use is 4 billion. This is the reason why we use the the prived in the LAN with one public IP in a LAN, this increases the IPv4 usage  
If all the LAN users use the internet will it work fine? Why?, Can all the users use the same public IP address at the same time?
the answer is **YES**, there's a protocal run in the **Network layer** called **NAT**(network address translation) that helps multiple devices on a private network(LAN) to share a single public IP address when connecting to the internet. This process is typically managed by a router or firewall, which translates private IP addresses into public ones and back again (you can read more about this protocol (NAT) [HERE](https://www.geeksforgeeks.org/network-address-translation-nat/)). 
