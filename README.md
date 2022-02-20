
![Coyote bot logo](https://pbs.twimg.com/profile_images/1437957467225268226/a_qfpwtb_400x400.jpg "Logo Coyote bot logo")
# AVAX Node Installer Tutorial

#### created by cedrik31tlse#8672 (Discord) / cedrik31tlse (Telegram)

Tutorial to create a node on Avalanche network (AVAX) to use with Coyote Chainsniper Linux Edition.

Link to official server of Coyote bots : https://discord.gg/fP3Z4tY92j

This tutorial helps to create a node on Avalanche network from a fresh install of Ubuntu 20.04.

1. Update all packages

```
apt update && apt upgrade -y
```

2. Create avax user

```
useradd -m avax
cd /home/avax
```

3. Download executable Avalanche

```
wget https://github.com/ava-labs/avalanchego/releases/download/v1.7.5/avalanchego-linux-amd64-v1.7.5.tar.gz
tar -xvf avalanchego-linux-amd64-v1.7.5.tar.gz
```

4. Edit starting script

```
nano start.sh
```

5. Paste thie content

```
./avalanchego-v1.7.5/avalanchego
```

6. Make file executable

```
chmod +x start.sh
```

7. Make service

```
nano /lib/systemd/system/avax.service
```

8. Paste the content

```
[Unit]
Description=AVAX Full Node
[Service]
User=avax
Type=simple
WorkingDirectory=/home/avax
ExecStart=/bin/bash /home/avax/start.sh
Restart=on-failure
RestartSec=5
[Install]
WantedBy=default.target
```

9. Chown files to avax user

```
chown -R avax.avax /home/avax/*
```

10. Start Node

```
systemctl enable avax
systemctl start avax
```

11. Check logs

```
journalctl -u avax
```
