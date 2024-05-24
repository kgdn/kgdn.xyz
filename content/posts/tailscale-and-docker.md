+++
title = 'Accessing local Docker containers through Tailscale'
date = 2024-05-23T16:35:28+01:00
toc = true
tags = ["docker", "tailscale", "vpn", "raspberry-pi"]
description = "How I use Tailscale to access my local Docker containers from anywhere"
categories = ["Technology"]
+++

In an attempt to make managing Discord bots and other services running on my home network easier, I've been experimenting with containerisation using Docker. Previously, when I had been managing my projects, especially the ones written in Python, I would run them on either my laptop or my headless Raspberry Pi, using `tmux` to keep them running in the background. This was fine for a while, but as I started to run more services, I found that it was becoming difficult to manage them all. So that's where Docker comes in.

## What am I running in Docker?

I'm currently running three to four services in Docker containers on my Raspberry Pi, including one or two Discord bots, a PostgreSQL database for said Discord bot, and [iSponsorBlockTV](https://github.com/dmunozv04/iSponsorBlockTV), a service that mutes sponsor segments in YouTube videos on the YouTube app on my Amazon Fire Stick.

Obviously, this is a small number of services, but it's enough to warrant using Docker to manage them. Can you imagine having to manage all of these services manually through `tmux`? It would be a nightmare, especially when it comes to restarting them.

## So what's the problem?

I can access these services on my local network just fine, but I wanted to be able to access them from anywhere, not just my local network. I could have just forwarded the ports on my router, but that would have been a security risk, as I would have had to expose the services to the internet. I had set up a VPN server on my Raspberry Pi using [PiVPN](https://www.pivpn.io/), but I found that it was a bit slow, unreliable and not very portable[^1]. So I decided to try out [Tailscale](https://tailscale.com/), a mesh VPN service that allows you to access your devices from anywhere, securely.

## How do we solve this?

This blog post isn't about setting up Tailscale, nor is it about setting up Docker. There are plenty of resources out there that can help you with that. Instead, I'll show you how my workflow has changed since I started using Tailscale and Docker.

### Setting up a Docker context

Docker has a feature called [contexts](https://docs.docker.com/engine/context/working-with-contexts/), which allows you to manage multiple Docker environments from a single CLI. In a hypothetical scenario where you have a Docker server running on a remote machine, you can use Docker context to manage the containers on that machine from your local machine. The commmand to set up a context is as follows:

```bash
docker context create raspberrypi --docker "host=ssh://pi@raspberrypi"
```

Great! At that point I had set up a context for my Raspberry Pi, which allowed me to manage the Docker containers on my Raspberry Pi from my laptop. Now this is all well and good if you're on the same network as your Raspberry Pi, but what if you're not? That's where Tailscale comes in!

### Setting up Tailscale

Tailscale allows you to access your devices from anywhere, securely, using a networking technique called NAT traversal. This means that you can access your devices as if they were on the same network as you, even if they're not. So, I set up Tailscale on my Raspberry Pi and my laptop, and I was able to access my Raspberry Pi from my laptop, even when I wasn't on the same network. That was as simple as running the `tailscale up` command on both devices, after installing the Tailscale client.

At this point, all I had to do was set up a context for my Raspberry Pi using the Tailscale IP address, and I was able to manage the Docker containers on my Raspberry Pi from my laptop, even when I wasn't on the same network.

```bash
docker context create raspberrypi --docker "host=ssh://raspberry.pi.tailscale.ip"
```

## Conclusion

Tailscale is an absolute game changer for me, as I can now manage my Docker containers from anywhere, without having to expose them to the internet. The same goes for the services running in the containers; I could access them from anywhere, securely.

Similarly, I could access the nginx server on my laptop, running a version of my bachelor's thesis project with proper SSL certificates, from any device on my Tailnet[^2].

[^1]: I was moving between my flat and my parents' house quite a bit at the time, and bringing my Raspberry Pi with me to act as a VPN server was a bit of a hassle. It also meant I had to have multiple SSH configurations for the same device in my `~/.ssh/config` file, which was a bit of a pain.

[^2]: Tailnet is the name of the network created by Tailscale.