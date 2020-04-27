Beginning with Moonlight Qt v2.0.0, support for L4T devices such as the [Nintendo Switch](https://gbatemp.net/threads/l4t-ubuntu-a-fully-featured-linux-on-your-switch.537301/) and NVIDIA Jetson development boards is in beta. As is typical with beta releases, the usual caveats apply: this may not perform well for you; it may crash/hang or just not work at all. Please [report bugs](https://github.com/moonlight-stream/moonlight-qt/issues) if you encounter issues.

Run the following commands to install Moonlight Qt to your L4T device:
```
echo "deb https://dl.bintray.com/moonlight-stream/moonlight-l4t bionic main" | sudo tee /etc/apt/sources.list.d/moonlight-l4t.list 
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61
sudo apt update
sudo apt install moonlight-qt
```

You can then launch Moonlight from your desktop or via the `moonlight-qt` command in the terminal.