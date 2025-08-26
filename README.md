# RPC

If you run your own RPC, you need to protect it from unauthorized connections and attacks. Most often, RPC is launched inside a Docker container, so to block IP, you need to use iptables with the -I DOCKER-USER flag.
