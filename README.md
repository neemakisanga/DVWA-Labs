# DVWA Docker Environment

This repository contains a Docker Compose configuration for running DVWA (Damn Vulnerable Web Application) for practicing OWASP Top 10 vulnerabilities.

## Project Structure

```
.
├── docker-compose.yml    # Docker configuration for DVWA
├── setup/                # Network configuration guides
│   └── host-networking.md # How to configure networking between host and Kali VM
├── exploits/             # Documentation for each exploit type
│   ├── sql-injection.md  # SQL injection techniques
│   └── brute-force.md    # Brute force attack techniques
└── reports/              # Vulnerability reports from your testing
    └── README.md         # Report templates and guidelines
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

## OWASP Top 10 Vulnerabilities to Practice

- Injection
- Broken Authentication
- Sensitive Data Exposure
- XML External Entities (XXE)
- Broken Access Control
- Security Misconfiguration
- Cross-Site Scripting (XSS)
- Insecure Deserialization
- Using Components with Known Vulnerabilities
- Insufficient Logging & Monitoring

## Exploit Guides

Check the [exploits](exploits/) directory for detailed guides on exploiting specific vulnerabilities:

- [SQL Injection](exploits/sql-injection.md)
- [Brute Force](exploits/brute-force.md)

## Reporting

Use the report templates in the [reports](reports/) directory to document your findings.

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