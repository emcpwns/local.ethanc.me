# About hyperion.lan

hyperion.lan is an Intel N100-based firewall appliance running OPNsense with 4 onboard Intel i226-V 2.5G RJ45 ports, allowing for multi-gigabit networking. As the core of the network this host is designed around simplicity and reliability, so OPNsense is installed bare-metal with no abstraction layers such as PVE, Docker, etc.

## WAN Failover
Spectrum provides primary WAN access with a "gigabit" (asymmetric) coaxial connection, which while fast, as a consumer-tier line is often subject to outages and packet loss. Using gateway groups and some simple firewall rules, T-Mobile's 5G network provides a surprisingly stable failover WAN connection when things get spotty.
![Outage alert from Spectrum](https://raw.githubusercontent.com/emcpwns/local.ethanc.me/refs/heads/main/img/Outage%202026-01-20%202.png)

![Outage graph from SmokePing](https://raw.githubusercontent.com/emcpwns/local.ethanc.me/refs/heads/main/img/Outage%202026-01-20.png)
The SmokePing graph above taken from artemis.lan illustrates a complete Spectrum outage from about 1PM EST until 4PM EST on Tuesday, January 20th. Although this event was completely mitigated thanks to the failover WAN, this would otherwise represent an entire half-day of lost work.