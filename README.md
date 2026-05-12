# IP Blocklist

Attackers IP list collected.

## blocklist.dat

One IP per line, plain text:

```
35.189.195.1
45.148.10.121
65.49.1.58
66.132.186.193
111.48.105.20
120.48.75.127
130.12.180.51
152.32.192.176
198.235.24.97
```

## Usage with hosts.deny

```bash
# Append to /etc/hosts.deny
while read ip; do echo "ALL: $ip" >> /etc/hosts.deny; done < blocklist.dat

# Or one-liner
sed 's/^/ALL: /' blocklist.dat >> /etc/hosts.deny
```

## Usage with iptables

```bash
while read ip; do iptables -A INPUT -s "$ip" -j DROP; done < blocklist.dat
```

## Whitelist

`whiteiplist.dat` contains IPs excluded from the blocklist (one per line, `#` for comments).

## License

MIT
