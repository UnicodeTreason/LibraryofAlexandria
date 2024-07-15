# Zabbix Notes

## Host Availability

- If item collection fail then recheck every UnreachableDelay (15s) until UnreachablePeriod is reached (60s), if FAIL mark host as unreachable

- If host is unreachable then recheck every UnavailableDelay (60s)

## Passive vs Active Items

### Passive Item Collection

Zabbix Server communicates to the Host via the IP/DNS configured in the Interface.

```mermaid
  sequenceDiagram
    Server->>PassiveItem: [10050] Please collect ItemX
    PassiveItem->>Server: [10051] Here is the data collected for ItemX
```

### Active Item Collection

Zabbix Server communicates to the Host via the IP/DNS configured in the Interface. The correct HostName MUST be configured in the Zabbix Agent configuration for this conversation to occur.

```mermaid
  sequenceDiagram
    ActiveItem->>Server: [10051] What do I need to collect? My HostName is X
    Server->>ActiveItem: [10051] HostNameX needs to collect ItemX
    ActiveItem->>Server: [10051] Here is the data for ItemX for HostNameX  
```
