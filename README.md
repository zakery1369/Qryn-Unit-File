# Qryn-Unit-File

## qryn systemd unit file

![Qryn](https://raw.githubusercontent.com/zakery1369/pics/master/Qryn.png)

1.Create the qryn.service in the following path.

```bash
nano /etc/systemd/system/qryn.service
```

2.Place its contents as follows.

```bash
[Unit]
Description=qryn service
After=network.target

[Service]
EnvironmentFile=/etc/default/qryn_env
Type=simple
User=root
ExecStart=qryn 

[Install]
WantedBy=multi-user.target
```

3.Create the qryn_env in the following path.

```bash
nano /etc/default/qryn_env
```

4.Place its contents as follows.

```bash
NODE_PORT=3100
CLICKHOUSE_SERVER="my.clickhouse.server"
CLICKHOUSE_AUTH="default:YOUR_PASSWORD"
CLICKHOUSE_DB="qryn"
```

5.Reload the systemd files.

```bash
systemctl daemon-reload
```

6.Start qryn.

```bash
systemctl start qryn
```
