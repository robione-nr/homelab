# Journal

A concise chronological record of significant homelab infrastructure, web, email, AI, and operational work.

Entries preserve decisions, architectural context, resulting state, and useful lessons rather than step-by-step troubleshooting.

## 2026

### May

---

**2026-05-13 — [Agent Collaboration Architecture](2026/2026-05-13.md)**  
Defined the early operating model for a local multi-agent environment built around Hermes/OpenClaw and locally hosted LLMs.

**2026-05-17 — [Private Connectivity and Service Integration](2026/2026-05-17.md)**  
Installed Tailscale on the NAS/Xubuntu system and verified it online.

**2026-05-27 — [Rack Server Architecture](2026/2026-05-27.md)**  
Formalized the Dell PowerEdge R630 as the core virtualization platform.

**2026-05-29 — [Compute and GPU Role Separation](2026/2026-05-29.md)**  
Refined the rack design around two different responsibilities: general infrastructure under Proxmox and a GPU-oriented system for AI compute.

**2026-05-30 — [Utility Server and Service Foundation](2026/2026-05-30.md)**  
Expanded the Python 3.11 multi-domain Utility Server used by VPS-hosted applications.

### June

---

**2026-06-08 — [Proxmox Remote Administration](2026/2026-06-08.md)**  
Brought Proxmox and Tailscale together as the practical remote-management foundation for the homelab.

**2026-06-11 — [Repository Reorganization](2026/2026-06-11.md)**  
Began reorganizing infrastructure and application work into project-oriented Git repositories.

**2026-06-12 — [VPS Project Layout](2026/2026-06-12.md)**  
Standardized VPS-hosted projects around `/var/www/<project>/`, separating public web content from application code, scripts, configuration, and documentation.

**2026-06-18 — [Homelab Repository Established](2026/2026-06-18.md)**  
Created the dedicated homelab documentation effort to capture architecture, diagrams, projects, operational decisions, and lessons learned.

**2026-06-19 — [Storage and AI Host Direction](2026/2026-06-19.md)**  
Defined the Supermicro SYS-1028GQ-TXR with four Tesla P100 SXM2 GPUs as the dedicated AI compute system alongside the Dell PowerEdge infrastructure.

**2026-06-22 — [Mail Architecture Documentation](2026/2026-06-22.md)**  
Documented the self-hosted mail stack built around Postfix, Dovecot, OpenDKIM, OpenDMARC, and SpamAssassin.

**2026-06-25 — [HA and Storage Architecture](2026/2026-06-25.md)**  
Refined the target Proxmox/Ceph architecture around shared storage and multiple virtualization hosts.

**2026-06-29 — [Second Proxmox Node](2026/2026-06-29.md)**  
Started integrating the Supermicro SYS-1028GQ-TXR into the Proxmox environment alongside the Dell R630 infrastructure.

**2026-06-30 — [Cluster Integration](2026/2026-06-30.md)**  
Completed the core integration work for the second Proxmox node.

### July

---

**2026-07-04 — [Shared Administrative Scripts](2026/2026-07-04.md)**  
Extended CephFS beyond application/storage use by establishing it as a shared location for administrative tooling.

**2026-07-18 — [Redundant Network Design](2026/2026-07-18.md)**  
Defined the physical network around two FortiGate 201E firewalls, two Arista 7010T-48 switches for general Ethernet traffic, and two Arista 7050SX-64 switches for the 10GbE/storage fabric.

**2026-07-20 — [Network Migration Strategy](2026/2026-07-20.md)**  
Worked through migration from the original `192.168.1.x` environment toward structured `10.x` networks while preserving a dedicated Ceph network.

### August

---

**2026-08-09 — [Dedicated 10GbE Storage Fabric](2026/2026-08-09.md)**  
Moved the network toward `10.0.1.0/24` for general infrastructure and `10.10.10.0/24` for dedicated Ceph traffic.

**2026-08-15 — [VPS-to-Homelab Database Replication](2026/2026-08-15.md)**  
Established working asynchronous replication from VPS MySQL 8.0.46 to MySQL 8.0.46 running in Kubernetes on Ceph RBD.

**2026-08-16 — [Homelab Web Serving Path](2026/2026-08-16.md)**  
Validated a Kubernetes web-serving stack using a shared Cilium ingress VIP with site content backed by CephFS.

**2026-08-17 — [AI Service Platform](2026/2026-08-17.md)**  
Consolidated the Kubernetes AI platform around Hermes on `p100-01`, llama.cpp inference, Supermemory, PostgreSQL/pgvector, ArangoDB, Mattermost, Obsidian/Git, and CephFS.

**2026-08-19 — [Bidirectional Database Path](2026/2026-08-19.md)**  
Converted MySQL replication to GTID auto-positioning and brought up the reverse homelab-to-VPS channel.

**2026-08-20 — [Agent Routing and Secret Boundaries](2026/2026-08-20.md)**  
Added an agent directory alongside the core Hermes documentation to separate role/capability discovery from individual agent prompts.

**2026-08-22 — [VPS–Homelab File Synchronization](2026/2026-08-22.md)**  
Designed the website synchronization path around Unison over SSH, controlled from the homelab utility LXC.

**2026-08-23 — [Agent Workflow and Memory Model](2026/2026-08-23.md)**  
With VPS↔homelab MySQL, email, and website synchronization functioning, attention shifted from connectivity to how agents should actually use the available information.

**2026-08-25 — [Mattermost Agent Gateway](2026/2026-08-25.md)**  
Completed the Mattermost-side team, bot, token, user, and channel associations needed for a multiplexed Hermes gateway.

**2026-08-31 — [Ceph Network Routing Correction](2026/2026-08-31.md)**  
Corrected the dedicated Ceph interfaces on the Proxmox nodes to use the actual `10.10.10.0/24` storage subnet rather than an overly broad `/8` mask.

### September

---

**2026-09-02 — [Hermes Gateway and Profile Architecture](2026/2026-09-02.md)**  
Validated Mattermost as the practical human-facing interface to Hermes and confirmed that gateway multiplexing was routing Jeeves into the `liaison` profile rather than merely presenting a different name over the base Hermes workspace.

**2026-09-03 — [RAG and Librarian Pipeline](2026/2026-09-03.md)**  
Brought the shared PostgreSQL/pgvector RAG system and Librarian ingestion path to an operational state and validated it with a real source.

**2026-09-08 — [Ming GGUF Conversion](2026/2026-09-08.md)**  
Converted the text path of InclusionAI Ming-flash-omni-2.0 into GGUF for the quad-P100 environment.

**2026-09-10 — [Ming Text, Image, and Video Port](2026/2026-09-10.md)**  
Advanced the Ming-flash-omni-2.0 llama.cpp port from a working text backbone to functional text, image, and video input on `p100-01`.

**2026-09-14 — [Continuous Unison Operation](2026/2026-09-14.md)**  
Stabilized the OpenRC-managed Unison synchronization service under the `admin` user.

**2026-09-27 — [Utility Server Migration](2026/2026-09-27.md)**  
Moved the VPS Utility Server from its older project path into `/var/www/common-assets/python/utility-server`.

**2026-09-28 — [xsrv-api Security Boundary](2026/2026-09-28.md)**  
Established `xsrv-api` as the controlled interface for agent access to CephFS-backed web projects and managed application databases.

**2026-09-29 — [Resource Gateway and Utility Consolidation](2026/2026-09-29.md)**  
Formalized CephFS as authoritative web-project storage and consolidated controlled access around `svc-utility` (CT 1500, `10.0.1.8`).

**2026-09-30 — [Synchronization Validation](2026/2026-09-30.md)**  
Continued validating the consolidated Unison service from `svc-utility`.

### October

**2026-10-01 — [Homelab Documentation Refresh](2026/2026-10-01.md)**
Validated the current Kubernetes, ingress, web, and AI service topology. Revamped repository text and mermaid diagrams around the running environment.

## Tags

`ai` `apache` `arista` `automation` `ceph` `cephfs` `cilium` `databases`
`dns` `email` `fortigate` `github` `gpu` `hardware` `hermes` `kubernetes`
`llama.cpp` `mattermost` `ming` `multimodal` `mysql` `networking`
`postgresql` `proxmox` `rag` `security` `storage` `supermemory` `tailscale`
`unison` `vps` `web` `xsrv-api`
