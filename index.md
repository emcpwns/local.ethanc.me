# About local.ethanc.me

`local.ethanc.me` is the FQDN used for properties on my LAN, and will generally be used interchangeably when I'm referring to my homelab and/or local network environment as a whole.
While `ethanc.me` is my registered domain name, `local.ethanc.me` is reserved for my private network, and not accessible to the public or listed on any public DNS servers.

![Server rack picture](https://raw.githubusercontent.com/emcpwns/local.ethanc.me/refs/heads/main/img/Homelab%20Rack.jpg)

## Infrastructure

| Name           | Description                         | Purpose                                                                              |
| -------------- | ----------------------------------- | ------------------------------------------------------------------------------------ |
| WANa           | `Spectrum` Hitron DOCSIS 3.1 Modem  | Primary WAN connection, coaxial.                                                     |
| WANb           | `T-Mobile` Arcadyan KVD21 5G Modem  | Secondary WAN connection, mobile.                                                    |
| hyperion.lan   | Intel N100-based Firewall Appliance | [OPNSense](https://opnsense.org/opnsense/)-based routing & switching + MWAN failover |
| helios.lan     | TP-Link Archer A7                   | [OpenWrt](https://openwrt.org/about) wireless access point                           |
| atlas.lan      | HP EliteDesk 1L PC                  | Low-power [Proxmox VE](https://pve.proxmox.com/wiki/Main_Page) Host                  |
| prometheus.lan | Dell PowerEdge R430                 | Rack-mount [Proxmox VE](https://pve.proxmox.com/wiki/Main_Page) Host                 |
| hephaestus.lan | Brother MFC-J5620DW                 | Network printer/scanner                                                              |


## Core Software

| Name                                                           | Description                                                                                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Proxmox VE](https://pve.proxmox.com/pve-docs/)                | PVE is a complete, open-source server management platform for enterprise virtualization. It tightly integrates the KVM hypervisor and Linux Containers (LXC), software-defined storage and networking functionality, on a single platform. PVE is the virtualization host of choice for my homelab due to it's community support and flexibility.      |
| [Debian](https://www.debian.org/doc/manuals/debian-reference/) | Debian is one of the oldest Linux distros still in active development, and one I've used in one way or another for over 14 years now. Because of its maturity, it's incredibly stable, and Debian 11 or 12 installs make up the bulk of my LXCs.                                                                                                       |
| [Docker](https://docs.docker.com/manuals/)                     | Docker and it's associated tools like docker-compose are a containerization suite that automate the deployment of applications, allowing them to run consistently across different environments. I use Docker whenever possible to simplify the process of keeping hosts patched and secured, and reduce the need for extra VMs/LXCs when unnecessary. |

### VM vs LXC vs Docker CT

| Virtual Machine (VM)                             | Linux Container (LXC)                     | Docker Container (dCT)                                       |
| ------------------------------------------------ | ----------------------------------------- | ------------------------------------------------------------ |
| Full hardware virtualization with its own kernel | OS-level container running on host kernel | Application-level container built on OS-level container tech |
| Very Strong Isolation                            | Strong isolation                          | Moderate isolation                                           |
| Lower performance from hypervisor overhead       | Near-native performance                   | Near-native performance                                      |
| Boots in several seconds to a minute.            | Boots in a few seconds.                   | Typically boots in less than a second.                       |
| Windows, BSD, Linux, etc.                        | Linux Only                                | Linux Only                                                   |


## Virtual Hosts

| Name          | Description   | Type | Purpose                                                                                                                                                                    |
| ------------- | ------------- | ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kastor.lan    | DNS           | LXC  | Runs [Unbound](https://nlnetlabs.nl/projects/unbound/about/) for recursive DNS & [PiHole](https://pi-hole.net/) for local DNS and query filtering.                         |
| aegis.lan     | Reverse Proxy | dCT  | Uses [Traefik](https://traefik.io/traefik) for local reverse-proxy, with [Cloudflare](https://www.cloudflare.com/application-services/products/ssl/) for SSL certificates. |
| hades.lan     | VPN & DDNS    | dCT  | Uses [DuckDNS](https://www.duckdns.org/about.jsp) for dynamic-DNS, & [WireGuard](https://www.wireguard.com/) for VPN connections.                                          |
| artemis.lan   | Monitoring    | LXC  | Runs [Smokeping](https://oss.oetiker.ch/smokeping/) to track and graph uptime of the local network and specific remote hosts.                                              |
| hermes.lan    | Monitoring    | LXC  | [Notifiarr](https://notifiarr.com/) server for Discord integration & to track the status of select hosts, displayed at [status.ethanc.me](https://status.ethanc.me/).      |
| iris.lan      | iPXE          | dCT  | Runs [Netboot.xyz](https://netboot.xyz/) for simple and fast iPXE network booting.                                                                                         |
| mnemosyne.lan | NAS           | LXC  | 1TB NVMe text-document storage NAS & [Samba](https://www.samba.org/) server                                                                                                |
| tartarus.lan  | NAS           | LXC  | 16TB HDD ZFS storage pool with 1TB NVMe L2ARC cache                                                                                                                        |
| hestia.lan    | IOT           | VM   | [HomeAssistant OS](https://www.home-assistant.io/) host and Z-Wave controller.                                                                                             |
| athena.lan    | Web           | LXC  | Runs [Dashy](https://dashy.to/), a web-based dashboard.                                                                                                                    |
| demeter.lan   | Web           | LXC  | Uses [Homebox](https://homebox.software/en/) for home inventory management.                                                                                                |
| metis.lan     | Web           | dCT  | [Kiwix Server](https://wiki.kiwix.org/wiki/Kiwix-serve) for offline reading of Wikipedia & other archives.                                                                 |
| dionysus.lan  | Media         | LXC  | [Jellyfin](https://jellyfin.org/) server for browsing and streaming local media.                                                                                           |
| olympus.lan   | Media         | LXC  | [Pterodactyl](https://pterodactyl.io/) panel for hosting/managing video game servers.                                                                                      |
| ares.lan      | Other         | dCT  | Runs [ArchiveTeam Warrior](https://tracker.archiveteam.org/) to assist in crowd-sourced virtual archiving.                                                                 |
| panacea.lan   | Other         | LXC  | Hosts a [Folding@home](https://foldingathome.org/about-2/) node to assist is crowd-sourced scientific research.                                                            |

*This list is not exhaustive and excludes short-term deployments and redundant hosts.*
