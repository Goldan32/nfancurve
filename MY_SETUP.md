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

Now the original author intends this to be a user service, I think it should be a system service. May need root access for these steps, idk.

- Clone the repo

```
git clone ssh://git@github.com/Goldan32/nfancurve /usr/local/share/nfancurve
```

- Create the symlinks

```
sudo ln -s /usr/local/share/nfancurve/temp.sh /usr/local/bin/nfancurve
sudo ln -s /usr/local/share/nfancurve/config /etc/nfancurve.conf
sudo ln -s /usr/local/share/nfancurve/nfancurve.service /etc/systemd/system/nfancurve.service
```

- Restart systemd daemon

```
sudo systemctl daemon-reload
```

- Enable and start the new service

```
sudo systemctl enable nfancurve
sudo systemctl start nfancurve
```

- ...
- Profit.
