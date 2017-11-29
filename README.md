#zbx_redis_template

Zabbix template for Redis (python)

### For use python version script
- [python](http://www.python.org/downloads/) 
- [redis-py](https://github.com/andymccurdy/redis-py)
- [psutil]


## Install
You can monitor your redis in zabbix agent mode.

In zabbix agent mode, zabbix will periodically send request to an agent for every parameter, and agent will answer it.

In trap-message mode, script will be periodically accumulate redis's parameters and will send it to zabbix as a one message.

If you planning to capture many redis parameters and do it often. I would recomend  to use trap-message mode.


### Install in Zabbix Agent mode

1) Put `zbx_redis.conf` into your `zabbix_agentd.conf` config subdirectory (like: `/etc/zabbix/zabbix_agentd.d/`).

2) Change script name in `zbx_redis.conf` to use `zbx_redis_stats.py` if need it .
Redis server params can be passed to the python script as arguments e.g.:
```
zbx_redis_stats.py localhost -p 6379 -a mypassword
```

3) Put `zbx_redis_stats.py` into your `zabbix_agentd.conf` config subdirectory (like: `/etc/zabbix/script/redis/`).

4) Change paths in `zbx_redis.conf` if need it.

5) In working dir (`/etc/zabbix/script/redis/`) do:

```
For use python verson script:
pip install redis
pip install psutil 
chmod +x zbx_redis_stats.py
```
7) Import `zbx_export_template.xml` into zabbix in Tepmplate section web gui.

### Upgrade

1) fix get dbsize bug

2) add get redis vmsize and vmsize ratio
