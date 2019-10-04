# Multiple connections error
If you get this warning, your host PC is probably connected to your home network via both WiFi and Ethernet. This can cause connection issues with NVIDIA GameStream. Disconnect one of the connections (preferably the WiFi connection), then try again.

# Connected through another router error
If you get this error, it usually means you have two routers plugged into each other. This is usually caused by having your own wireless router plugged into a router already provided by your ISP. This setup prevents many applications from working optimally, like hosting games, P2P applications, etc.

You can fix this by switching one of your two routers into bridged or Access Point mode. The steps to do this vary by router, but you should be able to find them by Googling around a bit.

If you're sure that you don't have more than one router running on your network, this error may be caused by a Carrier-Grade NAT running on the ISP's network. You can try the steps in the section below to resolve that.

If you can't fix this, you can try using the [ZeroTier setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#zerotier) instead.

# Carrier-Grade NAT error
If you get this error, your ISP hasn't given you a public IP address which allows you to host services like Moonlight on the Internet. In many cases, your ISP will be happy to give one to you for free if you just ask.

If your ISP won't give you a public IP address, you can try using the [ZeroTier setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#zerotier) instead.

# Limited connectivity for hosting error
If you get this error, your ISP hasn't given you a public IP address which allows you to host services like Moonlight on the Internet. In many cases, your ISP will be happy to give one to you for free if you just ask.

Despite the lack of a public IP address, your connection does offer IPv6 support which will work for hosting over the Internet but streaming will only work natively from networks that also support IPv6. You can check a network's IPv6 support by [running this test](http://test-ipv6.com/) while connected to the network you want to test. If it scores a 10/10, it should be good to go. If not, you may try the [Cloudflare 1.1.1.1 app for iOS and Android](https://1.1.1.1/) with the free 'WARP' feature to gain IPv6 connectivity on networks that don't natively support it.

If your ISP won't give you a public IP address, you can try using the [ZeroTier setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#zerotier) instead.

# Internet GameStream connectivity check error
This error usually means your router doesn't have UPnP enabled. Some routers have bugs where UPnP doesn't work properly, so you may check your router manufacturer's website for a firmware update for your router that could fix it. You can also try restarting your router.

This error may also be caused by a firewall product on your host PC blocking the Internet Hosting Tool from talking to your router. Try disabling your host PC's firewall temporarily to see if that's the cause.

If you can't fix this error, you can try using the [ZeroTier setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#zerotier) instead or you can [forward the ports manually](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#manual-port-forwarding-advanced) if you feel comfortable making changes to your router settings.