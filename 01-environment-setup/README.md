# Phase 1: Environment Setup

## Incus Container (osTicket Host)

| Setting         | Details               |
| --------------- | --------------------- |
| **OS**          | Debian 13             |
| **CPU**         | 2 vCPUs               |
| **RAM**         | 1 GiB                 |
| **Disk**        | 10GiB                 |
| **Network**     | 10.126.148.11         |
| **Web Server**  | Apache/2.4.66         |
| **PHP Version** | PHP 8.2.30            |
| **Database**    | 12.2.2-MariaDB-deb13  |



![Incus Container](screenshots/incus-container-osticket.png)

## Active Directory Structure

| OU            | Users                                        |
| ------------- | -------------------------------------------- |
| Management    | Bob Jones, Jane Doe, John Smith, Mark Strong |
| Accounting    | Alice Smith, Diana Prince, Jack Smart        |
| IT Department | Emma Stone, Oliver Brown                     |

![AD Users and OUs](screenshots/win-server-ad-users-ous.png)

## Windows 11 Client

Domain join confirmed. Domain users can log in from this machine to submit tickets from the end-user perspective.

![Domain Join](screenshots/win11-domain-join.png)

## Network Topology

![Network Topology](screenshots/network-topology-diagram.png)

## Notes

See  [[network-routing-config]] for IP addresses, hostnames, and container configuration details.
