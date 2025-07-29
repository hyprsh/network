# Prepare hosts


## 1. Install debian
Placeholder

## 2. Install docker
Placeholder

## 3. Install keepalived

```sh
echo "modprobe ip_vs" >> /etc/modules
modprobe ip_vs

# deploy global service
docker service create \
  --name keepalived \
  --mode global \
  --network host \
  --cap-add NET_ADMIN \
  --cap-add NET_BROADCAST \
  --env TZ=Europe/Berlin \
  --env KEEPALIVED_VIRTUAL_IP=192.168.1.11 \
  --env KEEPALIVED_VIRTUAL_MASK=24 \
  --env KEEPALIVED_CHECK_PORT=22 \
  --env KEEPALIVED_VRID=150 \
  --env KEEPALIVED_INTERFACE=enp6s18 \
  shawly/keepalived
```

## 4. Init swarm

```sh
docker swarm init
# add manager nodes
```

