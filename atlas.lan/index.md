# About atlas.lan


## Child Hosts

| Name          | Description   | Purpose                                                                                                                                                                    |
| ------------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| kastor.lan    | DNS           | Runs [Unbound](https://nlnetlabs.nl/projects/unbound/about/) for recursive DNS & [PiHole](https://pi-hole.net/) for local DNS and query filtering.                         |
| aegis.lan     | Reverse Proxy | Uses [Traefik](https://traefik.io/traefik) for local reverse-proxy, with [Cloudflare](https://www.cloudflare.com/application-services/products/ssl/) for SSL certificates. |
| hades.lan     | VPN & DDNS    | Uses [DuckDNS](https://www.duckdns.org/about.jsp) for dynamic-DNS, & [WireGuard](https://www.wireguard.com/) for VPN connections.                                          |
| artemis.lan   | Monitoring    | Runs [Smokeping](https://oss.oetiker.ch/smokeping/) to track and graph uptime of the local network and specific remote hosts.                                              |
| hermes.lan    | Monitoring    | [Notifiarr](https://notifiarr.com/) server for Discord integration & to track the status of select hosts, displayed at [status.ethanc.me](https://status.ethanc.me/).      |
| iris.lan      | iPXE          | Runs [Netboot.xyz](https://netboot.xyz/) for simple and fast iPXE network booting.                                                                                         |
| mnemosyne.lan | NAS           | 1TB NVMe text-document storage NAS & [Samba](https://www.samba.org/) server                                                                                                |
| hestia.lan    | IOT           | [HomeAssistant OS](https://www.home-assistant.io/) host and Z-Wave controller.                                                                                             |
| athena.lan    | Web           | Runs [Dashy](https://dashy.to/), a web-based dashboard.                                                                                                                    |


*This list is not exhaustive and excludes short-term deployments and redundant hosts.*
