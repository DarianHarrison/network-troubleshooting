# network-troubleshooting
a quick reference of things to try when troubleshooting networks

0. interface troubleshooting
```
ip -h netconf # provide local network config
ip addr show # provide physical and local network information
```
view physical/logical network information
```
ip addr show dev <eno0(physical)/virbr(logical)>
..
..
```

1. dns server troubleshooting

a) default configuration
```
cat /etc/resolv.conf | grep "nameserver"
```
nameserver 10.157.0.13
nameserver 10.157.0.53

b) query dns to verify
```
dig m2-ess-vm85.mip.storage.hpecorp.net
```

c) fetch dns records for a given domain name or ip addr
```
nslookup -type=any m2-ess-vm84
nslookup -type=any google.com
```


2. router troubleshooting

a) find router ip
```
netstat -nr | awk '$1 == "0.0.0.0"{print$2}'
```

b) can you ping your router ?
```
ping 10.163.168.1 # "echo" req
```

c) more router troubleshooting

hops = routers

traceroute -4 m2-ess-vm85.mip.storage.hpecorp.net # note: -4 means ipv4
traceroute -4 google.com # hops to the internet

3. can we reach port ?
```
telnet <ip> <port> # for tcp
nc -z -v -u [hostname/IP address] [port number] # for udp
```

4. general info 

```
cat /etc/hosts 
cat /etc/hostname
```
```
hostname
hostname -f
```
