# Install NodeJS Environment

## Local Server, Arch

-   httpd.conf

```
ProxyPass /dirname http://localhost:3000/

LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so`
```

-   run node app, then access at localhost/node

