---
title: DHCP
date: 2024-01-21T15:12
tags:
  - Networking
cssclasses:
---

Dynamic Host Configuration Protocol (DHCP) is a network management protocol used to automate the process of configuring devices on IP networks. It allows devices to receive IP addresses and other network configuration details, such as the default gateway and [[DNS]] servers, automatically from a DHCP server. This eliminates the need for manual configuration of IP addresses and reduces the risk of IP address conflicts.

![[DORA.png]]

Here’s a more detailed breakdown of how DHCP works:

1. **DHCP Discover**: When a device (client) connects to a network, it sends out a DHCP Discover message to identify any available DHCP servers on the network.

2. **DHCP Offer**: A DHCP server responds to the Discover message with a DHCP Offer message, which includes an available IP address and other network configuration details.

3. **DHCP Request**: The client responds to the DHCP Offer with a DHCP Request message, indicating that it intends to use the offered IP address and configuration.

4. **DHCP Acknowledgment**: The DHCP server sends a DHCP Acknowledgment message to confirm that the client can use the IP address and provides the final configuration details.

5. **Lease Renewal**: The IP address assigned to the client is leased for a specific period. The client must periodically renew the lease by sending a DHCP Request to the server before the lease expires.

*This Process is commonly referred to as **DORA***

DHCP simplifies network administration by dynamically assigning IP addresses and ensuring that each device on the network has a unique IP address. This is particularly useful in environments where devices frequently join and leave the network, such as in homes, offices, and public [[Wi-Fi|Wi-Fi]] networks.

