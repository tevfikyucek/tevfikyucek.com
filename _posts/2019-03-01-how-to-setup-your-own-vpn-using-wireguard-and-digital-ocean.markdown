---
layout: post
title: How to Setup Your Own VPN using WireGuard and Digital Ocean
date: '2019-03-01 03:40:55'
tags:
- internet-security
- privacy
---

[Virtual Private Network (VPN)](https://en.wikipedia.org/wiki/Virtual_private_network) is a must for accessing internet through public internet. &nbsp;One issue, however, is finding a good, reliable VPN provider that you can trust. [A recent article](https://hackernoon.com/whos-really-behind-the-world-s-most-popular-free-vpns-d74bafc82178) shows that most (59%) of the VPN service provider has Chinese backing. This is ironic that VPN is illegal in China :)

I used [ProtonVPN](https://protonvpn.com/) from time to time. It did the job for connecting to Airport Wi-Fi when I was travelling. However, I was wondering whether it would even be possible to run your own VPN server and my search took me to [WireGuard](https://www.wireguard.com/), a simple VPN server solution that one can host himself/herself. It is open-source and super simplistic with only 4000 lines of code. I followed the [a tutorial written by Graham Setevens](https://grh.am/2018/wireguard-setup-guide-for-ios/) (found online) to install WireGuard on the Digital Ocean droplet that is hosting this blog. There is an iOS application to connec to the server which is easy to configure and use.

So far, it has been working quite nicely and definetely worth the effort of installing and hosting my own VPN server.

