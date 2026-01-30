# About hyperion.lan

hyperion.lan is an Intel N100-based firewall appliance running OPNsense with 4 onboard Intel i226-V 2.5G RJ45 ports, allowing for multi-gigabit networking. As the core of the network this host is designed around simplicity and reliability, so OPNsense is installed bare-metal with no abstraction layers such as PVE, Docker, etc.

Spectrum provides primary WAN access with a "gigabit" (asymmetric) coaxial connection, which while fast, as a consumer-tier line is often subject to outages and packet loss. Using gateway groups and some simple firewall rules, T-Mobile's 5G network provides a surprisingly stable failover WAN connection when things get spotty.

