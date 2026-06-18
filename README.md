# Homelab Infrastructure

Personal infrastructure used to learn, build, and operate self-hosted services, virtualization, remote access, and AI workloads. Current efforts focus on migrating services from a VPS into the homelab while building toward highly available, containerized AI inference infrastructure.

As it stands currently:

## Architecture

```mermaid
flowchart TD

    Cloudflare[Cloudflare DNS]
    Tailscale[Tailscale Mesh]
    Laptop[Laptop Anywhere]

    subgraph VPS
        direction TD
        Web[Web Applications]
        MySQL[(MySQL)]
        Email[Email Server]
        Utility[Utility Server]
    end

    subgraph Homelab
        DellA[Dell PowerEdge R630]
        SM1028[Supermicro SYS-1028GQ-TXR]
        Proxmox([Proxmox Host])
        VMs@{ shape: docs, label: "Virtual Machines" }
        AIP@{ shape: docs, label: "AI Processes" }
    end

    Cloudflare --- Web
    Cloudflare --- Email
    Web --- Utility
    Web & Utility & Email --- MySQL

    Tailscale --- VPS & Homelab & Laptop

    DellA ---> Proxmox
    Proxmox ---> VMs
    SM1028 ---> AIP
```

## Environment

| Area             | Technology                          |
| ---------------- | ----------------------------------- |
| Servers | Proxmox VE, Ubuntu 22+ |
| Web Stack        | Apache, PHP, MySQL             |
| Utility Services | Python 3.10, systemd                |
| Email            | Postfix, Dovecot             |


## Objectives

* Learn VM deployment and management through Proxmox
* Develop an understanding of containerized workloads
* Develop AI inference infrastructure & self-hosted services
* Improve monitoring and automation
* Document lessons learned

## Repository Contents

| Folder    | Purpose                                      |
| --------- | -------------------------------------------- |
| journal/  | Build log, troubleshooting notes, milestones |

<sub>(Additions as needed.)</sub>

## Recent Milestones

* Integrated servers into home LAN.
* Tailscale setup and verified
* Expandec utility server functionality
* Reorganizing GitHub around infrastructure and project documentation
