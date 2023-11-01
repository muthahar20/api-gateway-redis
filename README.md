# api-gateway-redis
Api Gateway with Redis 6 Clusters configuration for load-balancing

# Redis Cluster Creation on local system

 Creating Folder Structure
  > mkdir 6001 6002 6003 6004 6005 6006
 Create redis.conf file with given details
> vim redis.conf

port 6001
cluster-enabled yes
cluster-config-file nodes.conf
cluster-node-timeout 5000
appendonly yes

-- Save it and exit

Copy redis.conf file and move into above folders and update port nubers according folder numbers
> cp redis.conf 6001/redis.conf
> cp redis.conf 6002/redis.conf
> cp redis.conf 6003/redis.conf
> cp redis.conf 6004/redis.conf
> cp redis.conf 6005/redis.conf
> cp redis.conf 6006/redis.conf

--Start each redis servers 

> cd 6001
>redis-server /opt/homebrew/etc/redis.conf

> cd 6002
>redis-server /opt/homebrew/etc/redis.conf

> cd 6003
>redis-server /opt/homebrew/etc/redis.conf

> cd 6004
>redis-server /opt/homebrew/etc/redis.conf

> cd 6005
>redis-server /opt/homebrew/etc/redis.conf

> cd 6006
>redis-server /opt/homebrew/etc/redis.conf


-- we started individual server now connectiong each other

>redis-cli --cluster creat 127.0.0.1:6001 127.0.0.1:6002 127.0.0.1:6003 127.0.0.1:6004 127.0.0.1:6005 127.0.0.1:6006 --cluster-replicas 1
> yes
-- check redis client by typing ping
> redis-cli -p 7000 -c
>ping

-- checking redis clusters 
> cluster slots
> cluster info



















