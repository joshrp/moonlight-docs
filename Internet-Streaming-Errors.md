# Connected through another router error
If you get this error, it usually means you have two routers plugged into each other. This is usually caused by having your own wireless router plugged into a router already provided by your ISP.

You can fix this by switching one of your two routers into bridged or Access Point mode. The steps to do this vary by router, but you should be able to find them by Googling around a bit.

If you're sure that you don't have more than one router running on your network, this error may be caused by a Carrier-Grade NAT running on the ISP's network. You can try the steps in the section below to resolve that.

If you can't fix this, you can try using the [ZeroTier setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#zerotier) instead.

# Carrier-Grade NAT error
If you get this error, your ISP hasn't given you a public IP address which allows you to host services like Moonlight on the Internet. In many cases, your ISP will be happy to give one to you for free if you just ask.

If your ISP won't give you a public IP address, you can try using the [ZeroTier setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#zerotier) instead.

# Internet GameStream connectivity check error
This error usually means your router doesn't have UPnP enabled. Some routers have bugs where UPnP doesn't work properly, so you may check your router manufacturer's website for a firmware update for your router that could fix it.

This error may also be caused by a firewall product on your host PC blocking the Internet Streaming Helper from talking to your router. Try disabling your PC's firewall temporarily to see if that's the cause.

If you can't fix this error, you can try using the [ZeroTier setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#zerotier) instead or you can [forward the ports manually](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#manual-port-forwarding-advanced).

# Manual Internet streaming test fails
If the testing tool thinks everything is working but can't confirm it due to your network setup, it will ask you to perform the test yourself. It is important to _not be connected to the same network as your PC_ when testing this. You should disconnect from your WiFi network and connect with another network like cellular data or mobile tethering.

If you already paired with your PC on your WiFi network, your PC should just appear online after connecting to a different network if it's working properly. Otherwise, you should type the IP address it gives you into Moonlight's Add PC dialog.

If you can't get it working, you can try using the [ZeroTier setup steps](https://github.com/moonlight-stream/moonlight-docs/wiki/Setup-Guide#zerotier) instead.