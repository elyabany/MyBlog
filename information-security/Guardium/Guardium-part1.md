قبل متبدا في مرحله installation يجب انك تتاكد ان البورتات PORTS ديه مفتوحه 
[](https://www.ibm.com/docs/en/guardium/11.4?topic=system-guardium-port-requirements)

```bash
# DB Server – Collector #

   DB Server – Collector

    **TCP 8443 - open from DB server to collector
    TCP 16016 – UNIX STAP, both directions, registration, heartbeat, and data (including IBM i S-TAP running in PASE)
    TCP 16017 – Windows/Unix CAS, both directions, templates and data
    TCP 16018 – UNIX S-TAP (TLS) and External S-TAP, both directions, registration, heartbeat, and data
    TCP 16019 – Windows/Unix CAS (TLS), both directions, templates and data
    TCP 16020 - From S-TAP agent Clear UNIX S-TAP connection pooling
    TLS 16021 - From S-TAP agent Encrypted UNIX S-TAP connection pooling
    TCP 8081 – Guardium Installation Manager, both directions, database server to collector/Central Manager
    TCP 9800 – Windows S-TAP using protocol 8, both directions, DB Server to Collector, S-TAP registration and data
    TCP 9801 – Encrypted (TLS) Windows S-TAP using protocol 8, both directions, DB Server to Collector, S-TAP registration and data**
```

```bash
# Collector – Aggregator (Secure Shell – SSL) #

    **TCP 22 – collector to aggregator, SCP data exports, both directions**
```

```bash
# Central Manager – Managed Devices # 

    **TCP 22 – SSH/SCP data transfers, both directions
    TCP 8443 – SSL, both directions
    TCP 8444 – SSL, STAP to GIM file upload
    TCP 3306 – MySQL, opened to specific sources (for instance, the Central Manager is open to all managed units; a managed unit is open to the Central Manager)
    TLS 8447 - Used for remote messaging service infrastructure**
```
