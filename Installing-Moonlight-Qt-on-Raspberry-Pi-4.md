Beginning with Moonlight Qt v2.0.0, Raspberry Pi 4 support is in beta. As is typical with beta releases, the usual caveats apply: this may not perform well for you; it may crash/hang or just not work at all. Please [report bugs](https://github.com/moonlight-stream/moonlight-qt/issues) if you encounter issues.

[Moonlight Qt](https://github.com/moonlight-stream/moonlight-qt) differs from [Moonlight Embedded](https://github.com/irtimmer/moonlight-embedded) in that it provides a graphical user interface for Moonlight (even without X running), while Moonlight Embedded is command-line only. If you experience issues streaming to your Pi, trying the other client might resolve the problem. You can have both clients installed at the same time and switch between the two by running `moonlight` (Moonlight Embedded) or `moonlight-qt` (Moonlight Qt).

Requirements:
- Raspberry Pi 4 (earlier Raspberry Pi models may not perform well with the current beta)
- Raspbian Buster

Run the following commands to install Moonlight Qt to your Raspberry Pi:
```
echo "deb https://dl.bintray.com/moonlight-stream/moonlight-raspbian buster main" | sudo tee /etc/apt/sources.list.d/moonlight-raspbian.list 
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61
sudo apt update
sudo apt install moonlight-qt
```

You can then launch Moonlight from your Raspberry Pi's desktop or via the `moonlight-qt` command in the terminal.