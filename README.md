# AD LDAP Reconnaissance and Splunk Detection Lab

## 1. Overview

This project provides a controlled cybersecurity lab for practicing Active Directory LDAP reconnaissance and reviewing related logs in Splunk.

The lab is designed for authorized training in an isolated environment.

## 2. Lab Architecture

| Component | Role | Lab IP |
|---|---|---|
| DC01 | Samba Active Directory Domain Controller | `172.20.0.10` |
| Attacker | LDAP reconnaissance workstation | `172.20.0.20` |
| Splunk | Log collection, search, and alerting | `172.20.0.30` |

Domain: `corp.internal`

Network: `172.20.0.0/24`

## 3. Prerequisites

- A working Labtainer installation.
- Docker Engine supported by the installed Labtainer version.
- Sufficient disk space and memory for all three containers.
- Access to the Docker Hub images published for this lab.
- A Splunk installation and distribution arrangement permitted by its license.

## 4. Repository Contents

- `config/`: Lab network and container configuration.
- `dockerfiles/`: Docker build definitions.
- `docs/`: Lab documentation.
- `scripts/`: Supporting scripts and validation helpers.
- `screenshots/`: Demonstration screenshots.

## 5. Setup

1. Install and verify Labtainer.
2. Clone this repository into the appropriate Labtainer labs directory.
3. Configure the lab to use the published Docker Hub images.
4. Start the lab using the command supported by the installed Labtainer version.
5. Verify that DC01, Attacker, and Splunk can communicate on the lab network.

Detailed, tested commands will be documented in the setup guide.

## 6. Exercise Outline

1. Verify name resolution and LDAPS connectivity.
2. Authenticate to the directory using the designated low-privilege lab account.
3. Perform authorized LDAP directory queries.
4. Review available logs in Splunk.
5. Validate the detection rules and document the observed results.

## 7. Detection Scope and Limitations

The current lab has demonstrated LDAPS connectivity between the attacker and the domain controller. Because LDAP traffic is encrypted with TLS, the contents of individual LDAP queries are not necessarily visible in the existing Samba logs.

Detection of specific LDAP search filters must be separately instrumented and validated. Do not assume that a rule matching a particular `objectClass` already detects those queries.

## 8. Security Notice

Use this environment only for authorized training in an isolated lab network. Do not expose the lab services directly to the public internet.

Use lab-only credentials and never reuse them in real environments.

## 9. Licensing

Review the licenses and redistribution terms for Labtainer, Splunk, and every included third-party component before publishing or redistributing images.

