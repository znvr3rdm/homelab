![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

# My Homelab

### 👋 Hi, I´m Franz and I´m currently learning how to setup my own homelab. Join me on my road to my own server!

This **repository** contains notes, setups and configurations for my applications and other services running on my homelab.

> ⚠️ Be aware, that I´m still learning and there might be mistakes in some files. I do my best to minimize mistakes and update the repo if needed.
> However, if you do spot a mistake, please report it to me. Thanks!

Feel free to use any here available notes and setups on your own server!  
Note: I´m currently not using all of the here published apps and services, so always check compatibility before cloning anything.

<br>

# 🏁 Goals

### Why go through this?

I think I speak for all IT-Guys when I say that, for most people, a homelab or an own server is absolute overkill. But if you´re like me, interested in tech and looking for a way to provide maximum security with no monthly sbscriptions a homelab can fix exactly those problems.

**Therefore my primary goals with this setup are:**

- learning how to self-host apps and services for daily use
- increasing security and privacy by storing data on my server
- learning how networks and services work in general
- and of course to have fun!

**Concrete goals of apps and services i want to host are:**

* [ ] Creating an entrypoint for other services

  * [ ] Creating and building treafik as a reverse-proxy
  * [ ] Creating and building cloudflared as the entrypoint
  * [ ] Configuring the required docker network

  ---
* [ ] Creating a monitoring service for docker containers with notifications

  * [ ] Creating and building the monitoring service
    * [ ] Choosing a monitoring service
  * [ ] [IF NOT INTEGRTED INTO MONITORING] Creating and building the notification service
    * [ ] Choosing a notification service
  * [ ] Configuring notifications

  ---
* [ ] Creating a VPN service with a web-gui and user-management

  * [ ] Choosing a VPN service

  ---
* [ ] Creating my own self-hosted SSO (Single-Sign-On)

  * [ ] choosing between authentik and authelia
  * [ ] configuring the SSO to my liking
  * [ ] Integrating every service with SSO

<br>

# 🖥️ My current setup:

I´m currently running most of the here published apps and services in a VM with Xubuntu as an OS. The VM is on my old gaming pc where I installed Proxmox VE on.

### Specs of the Proxmox-Host


| Operating-System | CPU               | RAM       | Motherboard               | SSDs    | HDDs  |
| ------------------ | ------------------- | ----------- | --------------------------- | --------- | ------- |
| Proxmox VE       | AMD Ryzen 7 5700x | 32GB DDR4 | Gigabyte B550 Gaming X V2 | 1x256GB | 1x4TB |

<br>

### Specs of the VM running docker


| Operating-System  | CPU/Cores | RAM   | SSDs | HDDs  |
| ------------------- | ----------- | ------- | :----- | ------- |
| Xubuntu (minimal) | 6 cores   | 8 GiB | 40GB | 250GB |

---
