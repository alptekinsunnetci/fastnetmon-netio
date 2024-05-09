```
# fastnetmon-netio

## Installation

Download the relevant file and place it in an appropriate location:

```bash
wget https://fastnetmon.netio.com.tr/fastnetmon-netio -O /usr/bin/fastnetmon-netio
```

Grant the file appropriate permissions:

```bash
chmod +x /usr/bin/fastnetmon-netio
```

Create a systemd unit file to run it as a service and paste the following content:

```bash
nano /etc/systemd/system/fastnetmon-netio.service
```

Contents of `/etc/systemd/system/fastnetmon-netio.service`:

```ini
[Unit]
Description=FastNetMon - netIO
After=network.target

[Service]
ExecStart=/usr/bin/fastnetmon-netio
Restart=always
User=nobody
Group=nogroup

[Install]
WantedBy=multi-user.target
```

Enable the service:

```bash
systemctl enable fastnetmon-netio
```

Start the service:

```bash
systemctl start fastnetmon-netio
```

## Setting up BGP with Your Router

To set up FastNetMon-netIO with your router for BGP, you will need the following information:

- FastNetMon-netIO IP: Your server's IP address
- ASN: 65090
- TCP Port: 179

Incoming prefixes are tagged with a 666 community tag.

You can use IP Tables on your installation server. Keep TCP port 8179 closed to the outside.
```
