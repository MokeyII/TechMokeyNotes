---
tags:
  - Networking
---
# What is a network and how does it work?

Let's talk Multiplayer Gaming and how networking effects that. Let's say you're doing some PvP in an MMO you play. You press your "Shield Slam" ability and Slam into the squishy caster.
But how exactly does that caster know he's been slammed by you? Well, follow that green line.

![[Pasted image 20241011150346.png]]

That simple action caused a course of things to happen. That keystroke or button click went trough your computer, was processed by your CPU, was spit out of your network interface
as a packet, pushed across a series of **Switches**, **Routers** and **Firewalls**, to a **Server** then through some more switches, routers and firewall. Into the casters modem
through the router/firewall, switch, through the wall jack and into their computer which then processed that packet and told the application, TAKE DAMAGE AND GET STUNNED!

# That was a small section of a network and the internet, so what does the internet look like in a whole?
The internet is just a series of Firewalls, Routers, Switches and Servers located all over the place that have IP addresses assigned to them. Here's what that would look like if you were to draw a map of every ISP routing device that is connected creating the internet.
![[Pasted image 20241011143357.png]]
So let's talk about your "Shield Slam". Let's say you live in the zoomed in section. And the person you are shield slamming lives on the other side of the world. Let's say he lives in the top left yellow at the red dot:
![[Pasted image 20241011144345.png]]
Your shield slam would have to travel in a path determined by routers through all of these devices or "**nodes**" To reach the server, the server would then do the math, then output that and travel through additional nodes to tell that caster he's been hit. And this all happens in fractions of a second. Within milliseconds. It's really nutty once you put it into perspective and draw it out.