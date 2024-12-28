

# History of VPN
## PPTP
[[Point-to-Point-Tunneling Protocol (PPTP)|Point-to-Point Tunneling Protocol (PPTP)]]
Imagine you’re sending a letter across town, but you don’t want anyone to see what’s inside. You could put your letter into a sealed, secure envelope. PPTP is like that sealed envelope, but for your online data. It creates a safe "tunnel" for information to travel between your device and a destination (like a website or an office network) over the internet.

People use this “[[Tunnel|Tunnel]]” because the internet is public, meaning anyone can see data sent openly without protections. PPTP was one of the early methods to secure this data, so it’s mostly about privacy. Although newer, more advanced protocols have been created since, PPTP was one of the first ways to make sure information stayed private online.

## VPN vs PPTP

A [[Virtual Private Network (VPN)|Virtual Private Network]] is the general idea — it’s a technology that creates a private, secure connection over the internet. Imagine a VPN as a private road that hides your data while it travels to a destination online, so no one can see what you’re sending or receiving.

**PPTP**, on the other hand, is just one type or “model” of VPN. It’s one of the older ways to create that private connection. PPTP has its own specific way of encrypting (or scrambling) your data, but it’s not as secure as newer VPN types, like OpenVPN or WireGuard.

## Available to the public
People and Businesses needed a way for people to connect securely to their work stuff from outside the office. Think of it like being able to access files on a work computer even when you're at home. Microsoft saw this need and came up with PPTP, which is a type of VPN. They built it into Windows so anyone with a computer could use it, which made it pretty popular.

Basically, PPTP was one of the first easy ways to create a “secure tunnel” for your internet data. Instead of your info just floating out there on the open internet, PPTP kept it private. And while it’s not super secure by today’s standards, it opened the door for more people to use VPNs and paved the way for all the better, newer ones we use now.

# Networking
## VLANs
Imagine you’re at a huge office building with lots of departments — like Sales, HR, and IT. Normally, everyone could just walk around and talk to anyone in any department. But sometimes you need to keep certain areas separate, like keeping HR and IT traffic apart for security reasons. A VLAN (Virtual Local Area Network) is like putting invisible walls up so that each department is its own private space, even though they’re still in the same building.

So with VLANs, you’re making virtual “rooms” within one big network so people in each room can talk to each other easily, but they won’t mix with people in other rooms unless there’s a “door” set up between them.

## Subnets

Now, let’s say each department has a lot of people. If they’re all trying to talk at once, things can get crowded, kind of like a big traffic jam. A subnet (short for _subnetwork_) is a way of breaking a big group into smaller, more manageable groups. It’s like dividing a department’s big room into smaller sections so that traffic flows more smoothly.

In a nutshell:

- **VLANs** are like separate virtual “rooms” inside a building, keeping different groups (like departments) apart.
- **Subnets** are like smaller sections inside those rooms, making sure people don’t all get jammed up.
## Routing
Imagine you have all these departments (VLANs) and sections (subnets) set up in your big office building. But sometimes, people from Sales need to talk to HR, or someone from IT needs to visit a specific section in another room. Here’s where routing comes in!

Routing is like having a smart security guard at every door who knows exactly how to direct people from one place to another without them getting lost. This “security guard” (the router) reads the destination on each person’s “pass” (data packet) and guides them to the right room or section.

## Zoning
Imagine that in your building, you have high-security areas, like a server room or a finance vault, where only specific departments or personnel (say, IT or finance staff) should have access. You don’t want just anyone wandering in and out. That’s where zoning comes in.

Zoning creates strict boundaries around these sensitive areas. It’s like adding special, locked doors that only open for people with the right permissions or passes.