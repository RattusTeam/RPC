# RPC

If you run your own RPC, you need to protect it from unauthorized connections and attacks. Most often, RPC is launched inside a Docker container, so to block IP, you need to use iptables with the -I DOCKER-USER flag.

## Step 1: Create a whitelist of your IP addresses

Replace X.X.X.X and Y.Y.Y.Y with the IP addresses of the nodes you want to allow access to.

```console
#Allow access from trusted IP addresses
iptables -I DOCKER-USER -s X.X.X.X -p tcp --dport 8545 -j ACCEPT
iptables -I DOCKER-USER -s X.X.X.X -p tcp --dport 3500 -j ACCEPT

iptables -I DOCKER-USER -s Y.Y.Y.Y -p tcp --dport 8545 -j ACCEPT
iptables -I DOCKER-USER -s Y.Y.Y.Y -p tcp --dport 3500 -j ACCEPT

#Access denied to all others IP addresses
iptables -A DOCKER-USER -p tcp --dport 8545 -j DROP
iptables -A DOCKER-USER -p tcp --dport 3500 -j DROP
```
