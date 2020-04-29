Beginning with Moonlight Qt v2.0.0, support for L4T devices such as the [Nintendo Switch](https://gbatemp.net/threads/l4t-ubuntu-a-fully-featured-linux-on-your-switch.537301/) and NVIDIA Jetson development boards is in beta. As is typical with beta releases, the usual caveats apply: this may not perform well for you; it may crash/hang or just not work at all. Please [report bugs](https://github.com/moonlight-stream/moonlight-qt/issues) if you encounter issues.

NOTE: If you installed an earlier preview version of Moonlight Qt prior to v2.0.0, you must switch to the official repository to receive the update to v2.0.0 and future updates. To do so, run the the commands listed in the installation section and then those listed in the updates section.

### Installation
Run the following commands to install Moonlight Qt to your L4T device:
```
echo "deb https://dl.bintray.com/moonlight-stream/moonlight-l4t bionic main" | sudo tee /etc/apt/sources.list.d/moonlight-l4t.list 
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61
sudo apt update
sudo apt install moonlight-qt
```

You can then launch Moonlight from your desktop or via the `moonlight-qt` command in the terminal.

### Updates
To update Moonlight Qt after you've installed it, run:
```
sudo apt update
sudo apt upgrade
```