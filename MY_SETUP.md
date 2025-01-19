# How to setup this script

## Prereqs

- I think it needs XOrg, try with Wayland some time
- NVIDIA drivers installed, can adjust fan speed manually
  - If can't -> `sudo echo "needs_root_rights=yes" > /etc/X11/Xwrapper.config`
- Cool your bits, not sure this is needed or takes effect
  - `/etc/X11/xorg.conf.d/nvidia.conf` is a new file, created based on [USAGE.md](USAGE.md)
  - `/usr/share/X11/xorg.conf.d/10-nvidia.conf` is a default Ubuntu file
  - `Option "Coolbits" "12"` may need to be written in one of them


## Creating the service

- Clone the repo

```
git clone ssh://git@github.com/Goldan32/nfancurve /home/goldan/.local/share/programs/
```

- Create the symlinks

```
sudo ln -s /home/goldan/.local/share/programs/temp.sh /usr/local/bin/nfancurve
sudo ln -s /home/goldan/.local/share/programs/config /etc/nfancurve.conf
sudo ln -s /home/goldan/.local/share/programs/nfancurve.service /etc/systemd/user/nfancurve.service
```

- Restart systemd daemon

```
systemctl --user daemon-reload
```

- Enable and start the new service

```
mkdir -p /home/goldan/.config/systemd/user/default.target.wants/
sudo chown -R goldan:goldan /home/goldan/.config/systemd/user
systemctl --user enable nfancurve
systemctl --user start nfancurve
```

- ...
- Profit.
