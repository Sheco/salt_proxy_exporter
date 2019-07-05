# Salt Proxy Exporter

This is a Prometheus Exporter which proxies requests through saltstack.

Doing this is useful when the devices you need to monitor are behind a firewall but saltstack is allowed, the exporter gets the web requests which include the minion id on the URL, then connects to that minion to execute a particular command.

# Usage

The script needs to bind itself to an address and a port, the default values are loaded from a yaml file on ```/etc/default/salt_proxy_exporter.yml```, a [sample config file](salt_proxy_exporter.yml) is included in this repository.

These values can be overriden using parameters on the command line.

```
usage: node_exporter_proxy [-h] [--address ADDRESS] [--port PORT]

optional arguments:
  -h, --help         show this help message and exit
  --address ADDRESS  Address to bind to
  --port PORT        Port to bind to
```

# Installation as a systemd service

The included [systemd service unit](systemd/salt_proxy_exporter.service) can be installed in /etc/systemd/system and enabled/started as usual.

```
# systemctl daemon-reload
# systemctl enable salt_proxy_exporter
# systemctl start salt_proxy_exporter
```

