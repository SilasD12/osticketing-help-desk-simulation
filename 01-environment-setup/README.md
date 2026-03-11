# Phase 1: Environment Setup

Document the infrastructure that supports this help desk simulation.

## What Goes Here

- **Incus container configuration** — OS, resource allocation, web server stack (Apache/Nginx, PHP, MySQL/MariaDB), network config
- **Windows Server 2025** — Domain name, OU hierarchy, user accounts created
- **Windows 11 client** — Domain join confirmation, ability to log in as different domain users
- **Network topology diagram** — How all three systems communicate, IP addresses, hostnames
- **`notes.md`** — IP addresses, credentials reference, container config details

## Screenshots to Capture

- osTicket admin dashboard after fresh install
- Active Directory Users and Computers showing OUs and users
- `ipconfig` / `ip a` output from each machine
- Successful domain join confirmation on Win11
- Browser accessing osTicket from the Win11 client
- Network topology diagram (draw.io, Excalidraw, or ASCII art)
