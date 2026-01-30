# About prometheus.lan

prometheus.lan is a Dell PowerEdge R430 dual-socket rack mount server, running Proxmox Virtual Environment. With older silicon under the hood, the R430 is not the most power efficient PVE host, but what it lacks in practicality it makes up for in 48 decently powerful vCores to divide among LXCs and VMs for daily tasks and random projects. 

![Dell R430 Diagram](https://github.com/emcpwns/local.ethanc.me/blob/main/img/R430%20Diagram.png?raw=true)

Four 4TB SAS Hard Drives in a ZFS pool with two mirrored vdevs and a 1TB NVMe L2ARC cache drive provide storage to the virtual environment, and user-level access is provided to the storage pool through tartarus.lan. An additional 512GB SSD is installed for booting PVE and storing ISOs & CT Templates. Under typical conditions prometheus.lan draws about 110-148w of power, which while high, provides the storage backbone for the entire LAN in the form of good ole' spinning rust.

## Child Hosts

| Name         | Description | Purpose                                                                                                         |
| ------------ | ----------- | --------------------------------------------------------------------------------------------------------------- |
| tartarus.lan | NAS         | [TurnKey File Server](https://www.turnkeylinux.org/fileserver) for NAS/[Samba](https://www.samba.org/)          |
| demeter.lan  | Web         | Uses [Homebox](https://homebox.software/en/) for home inventory management.                                     |
| metis.lan    | Web         | [Kiwix Server](https://wiki.kiwix.org/wiki/Kiwix-serve) for offline reading of Wikipedia & other archives.      |
| dionysus.lan | Media       | [Jellyfin](https://jellyfin.org/) server for browsing and streaming local media.                                |
| olympus.lan  | Media       | [Pterodactyl](https://pterodactyl.io/) panel for hosting/managing video game servers.                           |
| ares.lan     | Other       | Runs [ArchiveTeam Warrior](https://tracker.archiveteam.org/) to assist in crowd-sourced virtual archiving.      |
| panacea.lan  | Other       | Hosts a [Folding@home](https://foldingathome.org/about-2/) node to assist is crowd-sourced scientific research. |


*This list is not exhaustive and excludes short-term deployments and redundant hosts.*
