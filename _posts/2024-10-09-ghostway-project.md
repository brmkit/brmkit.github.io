---
title: ghostway project
layout: default
tags: [red team, infrastructures, redirector, opsec]
blog_post: true
---
# ghostway project
_how to use a free service to let your packet jump inside your redirector infrastructure... just a basic example on how to cover our tracks during engagements_

Whether you're already an expert in red team tactics or you're just dipping your toes into the offensive family, understanding what is and how to implement redirectors is vital.
## wtf is a redirector?
They're servers that are geolocated away from us and whose sole purpose is to "redirect" traffic to our main infrastructure (the C2 servers).
Redirector's infrastructure must be as scalable and automated as possible, regardless of how they're created. The only result we need to achieve is to protect the main attack infrastructure: the C2 server(s).

The reason is pretty simple, if the attacked infrastructure detects and blacklists IP/domain referred to our **first** redirector - the one directly connected to the target - **our C2 servers are not directly exposed**. This means we can change referring IP/domains relatively quickly while keeping the attack infrastructure up and running.
Also, if some really skilled defender would try to forge some strange request for our C2 server(s) we can try to implement some filtering rule to our jump chain in order to mitigate related risks. Not so easy but... you never know :)

As mentioned earlier, redirectors must be something that we can change pretty easily in order to not impact our operations, to do so they must be deployed using some IaC black magic: ansible, terraform, single cloud functions, lambda, azure dev tunnels... choice your poison and just drink.

To be honest, i wrote this blog post because recently I had a strange idea: use a **free** mesh-vpn service to manage the internal redirects of an hypothetical redirectors infrastructure. It started as one of many "educational purpose" project and ended up doing research and understand if I was able to automate it. Now I just want to share my journey. 

So, this blog post talks about the ZeroTier VPN service and how to use it to be able to implement some kind of redirection logic.

## hey packet, let's take a ride with my ZeroTier bus
But, what is ZeroTier?

>*ZeroTier is a virtual networking platform that creates secure, private networks over the internet. It enables easy setup of virtual LANs, encrypts all network traffic, and provides centralized management.*

The main idea is to use a free, easy-to-use service to set up a cloud-based VPN without worrying about the technical details. This setup allows our redirectors to talk to each other securely, ensuring that data from one point to another hops smoothly, encrypted and... with some spice added.

Think of ZeroTierVPN like setting up your own private version of the internet. It works through what we call "moons," which are special nodes that help connect your devices securely across different locations. These moons act like guides - they help your devices find each other so they can communicate directly. When a message is sent, the moons help make sure it reaches the right device, but they never actually see or handle the content inside. It's like having a GPS system for your data, where only the destination is known, and the rest remains private between the sender and receiver.

Nothing special, but worth a try in a simple redirectors configuration.

## protocol explained: ZeroTier
ZeroTier's protocol is pretty simple to understand because it works basically in few steps.
In order to explain this kind of functionality and how to "use" it we assume we have 2 endpoint in two different area in the world, endpoint A and endpoint B, that **must have public IP**.

**Endpoint A** wants to send packet to **endpoint B** via ZeroTier interface but doesn't know the B's public ip. That's perfect because we want to route all traffic through ZeroTier network.

1. **A** sends a packet to the upstream root (R), asking information for **B**
2. If **R** has direct link with **B**, it sends the packet to **B**. Instead, if **R** doesn't know **B** it forwards the packet to his upstream node, continuing until it finally reaches ZeroTier planetary root (which knows everyone!)
3. Once the packet reaches **B**, **R** sends to **A** informations on how to reach **B** directly (using UDP)
4. **A** with the information of **B** tries to do an [UDP hole punching](https://en.wikipedia.org/wiki/UDP_hole_punching) (NAT traversal). If UDP is open on **B** and it's allowed to do NAT traversal, **A** and **B** reach each-other directly in order to establish a peer-to-peer connection (faster)

This is a simple explanation on how ZeroTier works, obviously we don't like this kind of "_perfectly balanced and optimized algorithm_". We want to **use** this functionality in our redirectors infrastructure and, to do so, we have just to _stop that UDP_ message.

In facts, as [ZeroTier Documentation states](https://docs.zerotier.com/relay/), when UDP is blocked the Protocol just use a simple TCP relay... that's just another name for a redirect.

If we stop that UDP message we can stop that perfectly optimized method for peer-to-peer connection and, basically, every packet **must reach first the planetary root (or a common root server) before reaching the final destination**, and every passage is just another jump in our chain.

That's it, a redirector infrastructure with multiple jumps inside, where **we simply cannot define how many there are**.

## just an example: ghostway
But now, let's talk about code.

To show you how to implement ZeroTier as backbone for redirectors, I created a project called **ghostway** - and the name is definitely more interesting than the code itself. Basically it sets up three cloud VMs connected via ZeroTier, each acting as a redirector that securely forwards traffic down the chain explained earlier.
Terraform is used to quickly deploy the VMs, and Ansible performs configuration management tasks to build the chain. Each redirector uses the ZeroTier IP to manage jumps through a basic nginx configuration.

Nothing too complicated, but it serves the purpose.

[ghostway](https://github.com/brmkit/ghostway)

This is just a simple, minimalist and **maybe silly way** to implement a redirection infrastructure using some free services and a pretty basic OPSEC concept in mind. There are many ways to do the same things, some well-known, some less so.
It's up to you to choose your favorite cloud provider that let you use terraform but, keep in mind, in order to increase your jumps you can consider to use different cloud provider for each redirector, different regions, _block some IPs_... and so on :)

If you want to discuss them feel free to contact me, I am always ready to discuss and learn from the awesome cybersec community!