# About local.ethanc.me

`local.ethanc.me` is the FQDN used for properties on my LAN, and will generally be used interchangeably when I'm referring to my homelab and/or local network environment as a whole.
While `ethanc.me` is my registered domain name, `local.ethanc.me` is reserved for my private network, and not accessible to the public or listed on any public DNS servers.

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

## Virtual Hosts

| Name          | Description   | Purpose                                                                                                                                                                    |
| ------------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kastor.lan    | DNS           | Runs [Unbound](https://nlnetlabs.nl/projects/unbound/about/) for recursive DNS & [PiHole](https://pi-hole.net/) for local DNS and query filtering.                         |
| aegis.lan     | Reverse Proxy | Uses [Traefik](https://traefik.io/traefik) for local reverse-proxy, with [Cloudflare](https://www.cloudflare.com/application-services/products/ssl/) for SSL certificates. |
| hades.lan     | VPN & DDNS    | Uses [DuckDNS](https://www.duckdns.org/about.jsp) for dynamic-DNS, & [WireGuard](https://www.wireguard.com/) for VPN connections.                                          |
| artemis.lan   | Monitoring    | Runs [Smokeping](https://oss.oetiker.ch/smokeping/) to track and graph uptime of the local network and specific remote hosts.                                              |
| hermes.lan    | Monitoring    | [Notifiarr](https://notifiarr.com/) server for Discord integration & to track the status of select hosts, displayed at [status.ethanc.me](https://status.ethanc.me/).      |
| iris.lan      | iPXE          | Runs [Netboot.xyz](https://netboot.xyz/) for simple and fast iPXE network booting.                                                                                         |
| mnemosyne.lan | NAS           | 1TB NVMe text-document storage NAS & [Samba](https://www.samba.org/) server                                                                                                |
| tartarus.lan  | NAS           | 16TB HDD ZFS storage pool with 1TB NVMe L2ARC cache                                                                                                                        |
| hestia.lan    | IOT           | [HomeAssistant OS](https://www.home-assistant.io/) host and Z-Wave controller.                                                                                             |
| athena.lan    | Web           | Runs [Dashy](https://dashy.to/), a web-based dashboard.                                                                                                                    |
| demeter.lan   | Web           | Uses [Homebox](https://homebox.software/en/) for home inventory management.                                                                                                |
| metis.lan     | Web           | [Kiwix Server](https://wiki.kiwix.org/wiki/Kiwix-serve) for offline reading of Wikipedia & other archives.                                                                 |
| dionysus.lan  | Media         | [Jellyfin](https://jellyfin.org/) server for browsing and streaming local media.                                                                                           |
| olympus.lan   | Media         | [Pterodactyl](https://pterodactyl.io/) panel for hosting/managing video game servers.                                                                                      |
| ares.lan      | Other         | Runs [ArchiveTeam Warrior](https://tracker.archiveteam.org/) to assist in crowd-sourced virtual archiving.                                                                 |
| panacea.lan   | Other         | Hosts a [Folding@home](https://foldingathome.org/about-2/) node to assist is crowd-sourced scientific research.                                                            |

*This list is not exhaustive and excludes short-term deployments and redundant hosts.*
