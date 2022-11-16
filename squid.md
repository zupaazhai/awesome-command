# Squid

## Install squid on Ubuntu 20x
```
apt install squid
```

## Check service is running
```
systemctl status squid.service
```

## Install apache2-utils for generate password
```
apt install apache2-utils
```

## Create password
```
htpasswd -c /etc/squid/passwords username
cat /etc/squid/passwords
```

## Add auth config
open file /etc/squid/squid.conf
```
auth_param basic program /usr/lib/squid/basic_ncsa_auth /etc/squid/passwords
auth_param basic realm proxy
acl authenticated proxy_auth REQUIRED
...
http_access allow authenticated
```

## Restart service
```
systemctl restart squid.service
```

## Allow port 3128
```
ufw allow 3128
```

## Test proxy
```
curl -v -x http://zupaazhai:123456@localhost:3128 http://www.google.com/%
```
