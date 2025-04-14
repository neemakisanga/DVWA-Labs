# DVWA Docker Environment

This repository contains a Docker Compose configuration for running DVWA (Damn Vulnerable Web Application) and documentation from my exercises practicing OWASP Top 10 vulnerabilities.

## Project Structure

```
.
├── README.md                     # This overview
├── docker-compose.yml            # Docker configuration for DVWA
├── setup/                        # Network configuration guides
│   └── host-networking.md         # How to configure networking between host and Kali VM
├── reports/                      # Vulnerability reports and walkthroughs from my testing
│   ├── brute-force-walkthrough.md # My brute force testing journey
│   └── progress.md                # Tracking my testing progress
└── images/                       # Supporting images for reports
```

## Prerequisites

- Docker
- Docker Compose
- Kali Linux VM (for penetration testing)

## Usage

1. Start the DVWA container:

```bash
docker compose up -d
```

2. Access DVWA at http://localhost:80

3. Login with default credentials:
   - Username: `admin`
   - Password: `password`

4. When prompted to setup/reset the database, click on "Create / Reset Database"

## Network Setup

See the [host-networking.md](setup/host-networking.md) guide for detailed instructions on configuring the network between your Kali Linux VM and the Docker container.

## OWASP Top 10 Vulnerabilities Explored

This project focuses on hands-on exploration of vulnerabilities like:

- Brute Force (See [reports/brute-force-walkthrough.md](reports/brute-force-walkthrough.md))
- Command Injection (In Progress - Tracked in [reports/progress.md](reports/progress.md))
- SQL Injection
- Cross-Site Scripting (XSS)
- File Inclusion
- File Upload
- CSRF
- And others...

## Reporting

My detailed findings and walkthroughs for each vulnerability tested are documented in the [reports](reports/) directory.

## Stopping the Environment

```bash
docker compose down
```

To completely remove all data (including the database volume):

```bash
docker compose down -v
```

## Note

This is a deliberately vulnerable application for security training purposes. Do not expose this to the internet or any production environment. 