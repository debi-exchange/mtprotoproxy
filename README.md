# Async MTProto Proxy #

Fast and simple to setup mtproto proxy.

## Starting Up ##
    
1. `git clone -b stable https://github.com/alexbers/mtprotoproxy.git; cd mtprotoproxy`
2. *(optional, recommended)* edit *config.py*, set **PORT**, **USERS** and **AD_TAG**
3. `docker-compose up --build -d` (or just `python3 mtprotoproxy.py` if you don't like docker)
4. *(optional, shows telegram link to set the proxy)* `docker-compose logs`

## Channel Advertising ##

To advertise a channel get a tag from **@MTProxybot** and write it to *config.py*.

## Performance ##

The proxy performance should be enough to comfortably serve about 4 000 simultaneous users on
the VDS instance with 1 CPU core and 1024MB RAM.

## Advanced Usage ##

The proxy can be launched:
- with a custom config: `python3 mtprotoproxy.py [configfile]`
- several times, clients will be automaticaly balanced between instances
- using *PyPy* interprteter
- with runtime statistics exported for [Prometheus](https://prometheus.io/): using [prometheus](https://github.com/alexbers/mtprotoproxy/tree/prometheus) branch

## 使用注意 ##
1. 如果作为APP内置代理，AD_TAG 不能设置，设置后无法登录
2. 建议使用 systemd 来启动 mptrotoproxy

- `cp mtproxy.service /etc/systemd/system/`
- `systemctl daemon-reload`
- `systemctl restart mtproxy.service`
- `systemctl status mtproxy.service`
- `systemctl enable mtproxy.service`
