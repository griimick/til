# Monitor udev events

Udev is a device manager for the Linux Kernel. It manages _device nodes_ in the `/dev` directory. Also, udev handles all the _user space_ events emitted when a harware device is attached or removed from the system.

`udevadm` - udev management tool

```
udevadm monitor
```
This utility will show you live udev events raised on hardware detection or when existing ones are removed. That is, one can see the udev events which will be emitted after this command has been run.

But, what if you want to see all the list of udev events that were emitted during the system boot process. I wanted to see the events raised when the internal soundcard is detected by Linux.
I wrote a simple systemd service to log all the udev events in a temporary file on startup.

```
[Unit]
Description=udev Logger
DefaultDependencies=no
Wants=systemd-udevd.service
After=systemd-udevd-control.socket systemd-udevd-kernel.socket
Before=sysinit.target systemd-udev-trigger.service

[Service]
Type=simple
ExecStart=/bin/sh -c "/bin/udevadm monitor > /tmp/udevadm-monitor.log"

[Install]
WantedBy=sysinit.target
```

- Save this systemd service as `/etc/systemd/system/udev-logger.service`
- Reload system daemon using `sudo systemctl daemon-reload`
- Enable the service using `sudo systemctl enable udev-logger.service`
- Start the service using `sudo systemctl start udev-logger.service`

All the udev events are logged in the `/tmp/udevadm-monitor.log`. 

- To stop and disable the service, run
```
sudo systemctl stop udev-logger.service && sudo systemctl disable udev-logger.service
```
