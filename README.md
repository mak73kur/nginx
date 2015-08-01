# CONNECT HTTP method for nginx

Module http_proxy_connect_module is enabled by default when compiling nginx from sources.

```
./auto/configure ...
make && make install
```

Add following settings directives to your server configuration to enable method CONNECT for ssl tunneling:

```
    server {
        listen       80;
        server_name  localhost;

        proxy_connect;
        proxy_connect_allow 443;
        
        resolver               8.8.8.8 valid=300s;
        resolver_timeout       10s;
    }
```

Module code from here https://github.com/alibaba/tengine/commit/7a4177b139d5fada2d46c808ba3f9e6b5d14121c

Adapted from https://github.com/lark/tengine/tree/proxy-connect
