# network-troubleshooting
a quick reference of things to try when troubleshooting networks

## 0. interface troubleshooting
```bash
ip -h netconf # provide local network config
ip addr show # provide physical and local network information
```
view physical/logical network information
```bash
ip addr show dev <eno0(physical)/virbr(logical)>
..
..
```

## 1. dns server troubleshooting

a) default configuration
```bash
cat /etc/resolv.conf | grep "nameserver"
```
Server:		127.0.0.53

b) query dns to verify
```bash
dig lion10.com
```

c) fetch dns records for a given domain name or ip addr
```bash
nslookup -type=any lion10.com
nslookup -type=any google.com
```


## 2. router troubleshooting

a) find router ip
```bash
netstat -nr | awk '$1 == "0.0.0.0"{print$2}'
```

b) can you ping your router ?
```bash
ping <ip-from-previous-command>
```

c) more router troubleshooting

hops = routers

traceroute -4 lion10.com # note: -4 means ipv4
traceroute -4 google.com # hops to the internet

## 3. can we reach port ?
```bash
telnet <ip> <port> # for tcp
nc -z -v -u [hostname/IP address] [port number] # for udp
```

## 4. general info 

```bash
cat /etc/hosts 
cat /etc/hostname
```
```bash
hostname
hostname -f
```
