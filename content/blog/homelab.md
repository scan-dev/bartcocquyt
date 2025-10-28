---
title: "Homelab"
draft: false
cover:
  image: img/main-cover.png
  alt: 'homelab'
  caption: 'Homelab'
tags: ["html", "css"]
categories: "blog, homelab"
---

# 🚀 5‑Year's a Homelab: The Ultimate Playground for AI, IaC, and Edge Computing

> “A homelab is not a hobby; it’s a laboratory for the future.” – *Inspired by the ethos of the open‑source community.*

For more then five years, I’ve been building, tearing down, and re‑building a lab that’s become my personal sandbox for everything.

From AI research to Infrastructure‑as‑Code (IaC) experimentation. 
It’s a living, breathing ecosystem that pushes the limits of my hardware, software, and curiosity. 

Below is a deep dive into the heart of my homelab, the tech stack that fuels it, and how each component.
It is the stepping‑stone toward mastering tomorrow’s computing paradigms.

---

## The Operating System Journey - Insight

*For more than three years, my home computer has run on **Arch Linux** with a modern, eye‑pleasing desktop called **Hyprland**. I chose Linux over Windows long before most people even heard of it, and I’ve never once thought about switching back.*

### A Personal Commitment 💪

When I first moved into my own space, I wanted a system that would grow with me, not with a company’s software updates. I found that Linux gave me exactly that freedom.  

- I installed Arch Linux because it’s the most flexible, “do‑it‑yourself” operating system around.  
- The base installation is lean, with only the software I need—no extra programs that slow things down.  
- Every time I update my system, I get the newest improvements immediately, without having to wait for a big upgrade.
- Highly customizable with a looks/feel and needs that suite me and not something pushed upon users by the big technology corporations.

### A Desktop That Feels Like Home 🏠  

Hyprland is my Wayland‑based desktop environment. It’s built to be fast, simple, and highly customizable.  

- The windows “tiling” layout is similar to what I liked about i3, but with smoother animations and a cleaner look.  
- I can change how my display looks with a single text file, so I can switch from full‑screen gaming to a multi‑monitor workspace in a flash.  
- Input devices (mouse, touchpad, keyboard) feel responsive because the system uses a modern driver that works with Wayland.  
- Audio is handled by a lightweight service that lets me play music, record, or run voice assistants with minimal lag.

### Why Linux Stays My Choice 🌱  

- **Speed and Efficiency** – My computer runs faster when I use the open‑source drivers that Linux offers, especially for my graphic card.  
- **Control and Privacy** – I can keep everything on my machine, from running local AI models to rendering the desktop, without sending data to external servers.  
- **Community Support** – The Arch community is huge and helpful. If I run into a problem, I can find solutions on the Arch Wiki or ask on forums, and the fixes are often ready in days.  
- **No Microsoft** – I never wanted the feel of Microsoft Windows again. I’ve learned to use my machine in a way that feels natural and powerful, and I’m proud of the freedom that Linux gives me.

> *Read more:* Arch Wiki – *Getting Started* (2024) – <https://wiki.archlinux.org/title/Installation_guide>  

By building my homelab on **Arch Linux with Hyprland**, I’ve created a personal computing experience that’s as smooth as it is powerful. Every tweak, every update feels like a small win, and I’ve never imagined using a closed‑source operating system again.🌟

---

## 1️⃣ Hardware – The Foundation of Experimentation

| Category | Model | Specs | Role |
|----------|-------|-------|------|
| **Personal Workstation** | AMD Ryzen 5 7600X | 64 GB 6000 MHz RAM, Radeon RX 6800 XT, 2 NVMe (3 TB total) | Development, AI inference, UI hosting |
| **Networking** | Ubiquiti UniFi Dream Machine SE (UDM‑SE) | - | Edge router & firewall |
| | USW‑10Gb (Aggregation) | 10 GbE uplink | Core switching |
| | USW‑24 G2 | 24‑port Gigabit | Access layer |
| | USW‑Flex mini (x4) | 4‑port | Edge / PoE distribution |
| | UniFi AP (x3) | Wi‑Fi 6E | Wireless coverage |
| **Compute Cluster** | SUN X4271 (x2) | Dual‑CPU, 96 GB RAM | High‑performance workloads |
| | HP DL360 G7 (x4) | Dual‑CPU, 368 GB RAM total | Legacy high‑density servers |
| | HP Dual‑Managed L2/L3 Switch | 24 ports Gigabit switching | Data‑center networking |
| **Edge & Low‑Power** | Raspberry Pi Cluster | 7 CM3, 2 Pi 5 4 GB, 2 Pi 4 4 GB, 1 Pi 400 4 GB, numerous Pi Zero | Edge computing, low‑power experiments |
| | NVMe‑Hat & Halo Compute | – | Storage‑centric Pi 5 workloads |

> **Why this mix?**  
> *The high‑end workstation handles interactive AI and UI workloads, while the enterprise‑grade servers provide the compute density needed for heavy‑lifting tasks. The Raspberry Pi swarm is the “edge” playground, letting me prototype IoT, AI inference on low‑power devices, and test IaC on ARM.*

---

## 2️⃣ Networking – Unified, Flexible, and Scalable

All traffic funnels through the UDM‑SE, which offers robust firewalling, VPN, and SD‑WAN capabilities. From there, the 10 GbE aggregation switch stitches everything together, feeding into the 24‑port core and the PoE‑capable Flex minis. The result? **Zero broadcast storms, low latency, and full network isolation** for experimental labs.

*Documentation:*  
- UDM‑SE Setup Guide – Ubiquiti  
- USW‑10Gb – Ubiquiti Docs  
- PoE Power Planning – Ubiquiti Knowledge Base  

---

## 3️⃣ Software Stack – Turning Hardware into a Living Lab

### 3.1 Docker Swarm on the Raspberry Pi Cluster  
The Pi cluster runs a lightweight Docker Swarm orchestrator, hosting the following services:

| Service | Purpose | Notes |
|---------|---------|-------|
| **Homepage** | Service dashboard | main dashboard |
| **Uptime‑Kuma** | Availability monitoring | Real‑time alerts |
| **Portainer** | Docker management | Easy GUI |
| **Grafana** | Metrics & dashboards | Pulls from Prometheus |
| **File‑Browser** | File sharing | Web‑UI for Pi storage |

*Why Swarm?*  
Docker Swarm’s simplicity and built‑in HA make it ideal for a small cluster where you need zero‑config resilience. It also gives me a real‑world playground for IaC scripts that deploy to edge nodes.

### 3.2 Personal Workstation Services  

| Service | Role | Tech Stack |
|---------|------|------------|
| **Ollama** | AI inference (multiple models) | Local LLM hosting |
| **Open‑WebUI** | Web‑front for Ollama | FastAPI + Vue |
| **SearxNG** | Decentralized search engine | Python/Django |
| **GitLab CI/CD** | Centralize code base & Automation pipelines | GitLab Runner (Docker) |
| **Authentik** | Identity & access management | Django + OAuth |
| **Prometheus** | Metrics scraping | Node‑exporter + custom exporters |
| **Kasm** | Sandbox containers | Chromium + VNC |

> **Learning Outcomes:**  
> - **AI**: Running LLMs locally on a GPU gives hands‑on insight into inference latency, memory usage, and model optimization.  
> - **IaC**: GitLab CI/CD pipelines drive automated provisioning of Docker Swarm services, enabling repeatable deployments.  
> - **Edge**: Prometheus metrics collected from Pi nodes reveal power consumption, CPU temperature, and network throughput—essential data for edge‑aware design.

---

## 4️⃣ Automation & Power Management – The “Smart” Side

I built a **Node‑RED** flow that interfaces with the HP servers’ iLO and the Raspberry Pi’s GPIO to control power states. The flow:

1. **Monitors CPU load** (via Prometheus).  
2. **Decides** whether to power down idle nodes.  
3. **Sends** SSH commands or iLO APIs to shut them off.  

This not only saves electricity but also protects hardware from over‑use during idle periods.

---

## 5️⃣ Why This Homelab Matters

| Domain | What I Learn | Real‑World Impact |
|--------|--------------|-------------------|
| **AI** | Model inference on GPU, fine‑tuning, LLM deployment | AI democratization, privacy‑first inference |
| **IaC** | Terraform, Ansible, GitLab pipelines | DevOps automation, reproducible environments |
| **Edge Computing** | ARM inference, low‑power networking, real‑time data collection | IoT, 5G edge, distributed AI |
| **Networking** | VLANs, QoS, SD‑WAN | Enterprise network design, resilience |
| **Monitoring** | Prometheus/Grafana dashboards, alerting | Operations reliability, observability |

> *Research Corner:*  
> 1. **Edge AI Deployment** – *IEEE Internet of Things Journal* (2023)  
> 2. **IaC for DevOps** – *Kubernetes & Docker: A Hands‑On Guide* (O’Reilly, 2021)  
> 3. **Power‑Efficient Data Centers** – *ACM Digital Library* (2019)

These experiments keep me at the cutting edge of technology, turning every tweak into a potential research paper or open‑source contribution.

---

## 6️⃣ Future Horizons – Where I’m Going Next

| Goal | Planned Upgrade | Why |
|------|-----------------|-----|
| **Edge AI** | More Pi 5 with **Neural Compute Sticks** | Run YOLOv8 on ARM |
| **Serverless** | Deploy **K3s** on the cluster | Micro‑service scaling |
| **Edge Analytics** | Install **Apache Kafka** on Pi cluster | Stream processing at the edge |
| **GPU‑Scale** | Add a second **RX 6800 XT** | Larger LLMs, GPU‑cluster experiments |
| **Hybrid IaC** | Terraform + Ansible for network config | Declarative network provisioning |

---

## 6️⃣ Closing Thoughts

My homelab is **more than a collection of gadgets**. It’s an ever‑evolving laboratory that has taught me the fundamentals of **AI, IaC, and edge computing**—and more importantly, how to iterate fast, fail quickly, and learn from real‑world constraints. The knowledge gained here translates directly into:

- **Better DevOps pipelines** that can be scaled to corporate data centers.  
- **Smarter edge devices** that consume less power while delivering more intelligence.  
- **Privacy‑preserving AI** that runs locally without sending data to the cloud.

If you’re considering building your own homelab, start small, iterate fast, and let the hardware and software talk to each other. The future is hands‑on, and the best way to stay ahead is to *experiment*—and that’s exactly what my 5‑year‑old homelab has taught me.

---

## 📚 References & Resources

1. **Ubiquiti UniFi Docs** – <https://help.ui.com/hc/en-us>  
2. **Docker Swarm Documentation** – <https://docs.docker.com/engine/swarm/>  
3. **Prometheus Official Site** – <https://prometheus.io/docs/>  
4. **Node‑RED Official Docs** – <https://nodered.org/docs/>  
5. **Ollama GitHub** – <https://github.com/ollama/ollama>  
6. **Open‑WebUI GitHub** – <https://github.com/open-webui/open-webui>  
7. **SearxNG** – <https://github.com/searxng/searxng>  
8. **Authentik** – <https://github.com/goauthentik/authentik>  
9. **Kasm** – <https://github.com/kasmtech/kasm>  
10. **IEEE IoT Edge AI Survey** – *IEEE Internet of Things Journal*, 2023.  

> *All configurations are version‑controlled in my GitLab setup*  

---

## **Takeaway:** 
> A homelab is your personal testbed for the next wave of technology. Build it, break it, rebuild it, and let curiosity be your guide. Happy Lab-in'! 🚀

---

vmlab blog (c) 2025