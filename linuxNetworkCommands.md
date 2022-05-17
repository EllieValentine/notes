# Linux Network Commands

## host

DNS query

> host google.com

## netstat

Network information

| Option             | Description                                        |
| ------------------ | -------------------------------------------------- |
| -t or --tcp        | Display TCP information.                           |
| -u or --udp        | Display UDP information.                           |
| -r or --route      | Display the routing table.                         |
| -v or --verbose    | Verbose; display additional information.           |
| -i or --interfaces | Display information based on a specific interface. |
| -a or --all        | Apply to all.                                      |
| -s or --statistics | Display statistics for the output.                 |

> netstat -ta

## nslookup

simple DNS queries

> nslookup google.com
