# Install NodeJS Environment

## On Local Server, Arch

-   httpd.conf

```
ProxyPass /dirname http://localhost:3000/

LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so`
```

-   run node app, then access at localhost/node
-   make systemd unit file, /lib/systemd/system/my-node-app.service

```
[Unit]
Description=app.js
Documentation=localhost/node
After=network.target

[Service]
Environment=NODE_PORT=3000
Type=simple
User=nobody
ExecStart=/usr/bin/node /node/app.js

[Install]
WantedBy=multi-user.target
```

-   Run this service

```
systemctl --system daemon-reload
systemctl enable my-node-app.service
systemctl start my-node-app.service
```

## On GCP, Debian Server

-   Everything was same as in local server except server configuration
-   Apache2 Mods for proxy

```
me@gcp:/etc/apach2/mods-enabled$ sudo ln -s ../mods-available/proxy.loa
me@gcp:/etc/apach2/mods-enabled$ sudo ln -s ../mods-available/proxy.load
me@gcp:/etc/apach2/mods-enabled$ sudo ln -s ../mods-available/proxy_http.load .
```
