# Download CheckPoint VPN Client

* [Installation](#installation)
* [Core Features](#core-features)
* [Setup and Configuration](#setup-and-configuration)
* [Troubleshooting Guide](#troubleshooting-guide)
* [Advanced Configurations](#advanced-configurations)

## Installation

Download the latest version from Releases page:       
https://github.com/gridlock/CheckPoint-VPN-Client/releases/tag/88.30

After downloading, launch the installer and follow the step-by-step setup process. You'll review and accept the license agreement, select where to install the program, and define basic configuration options. Once installed, start the VPN Client, enter the gateway address, and sign in using your credentials. This will create a secure VPN tunnel that allows you to safely access internal systems.

### Steps to Install the Check Point Remote Access VPN Client:

1. **Activate the IPsec VPN Software Blade**:

   * Open SmartConsole.
   * Right-click the Security Gateway object and click `Edit`.
   * In the Network Security tab, enable the `IPsec VPN` feature.

2. **Include in Remote Access VPN Community**:

   * Go to the VPN Communities section within SmartConsole.
   * Add the selected Security Gateway to the Remote Access VPN Community.

3. **Set Up Authentication Methods**:

   * Inside the Security Gateway settings, open `VPN Clients > Authentication` and configure the desired authentication mechanisms.

4. **Apply the Access Control Policy**:

   * Push the updated Access Control Policy to the Security Gateway.

5. **Provide VPN Client Package to Users**:

   * Distribute the VPN installation package and access credentials (including the server URL) to the end users.

6. **Validate Remote Connectivity**:

   * Ensure a remote user can successfully establish a connection using the client.

### Establishing a Secure Connection

#### How Remote Users Communicate with the Security Gateway

A VPN tunnel allows remote users to securely access resources behind a Security Gateway. During the IKE exchange:

* Both sides authenticate using certificates, either issued by an Internal Certificate Authority (ICA) or an external Public Key Infrastructure.
* After a successful handshake, a secure communication tunnel is established between the client and the gateway.
* Traffic is encrypted using IPsec protocols, ensuring secure and tamper-proof communication.

#### Remote Access VPN Process Overview

1. Enable and configure the Security Gateway to accept remote access.
2. Add remote user profiles to the Security Management Server.
3. Define firewall policies and choose encryption protocols.
4. Use LDAP or user groups to manage policy application.
5. Configure encryption details inside the VPN community and enforce them.

### System Requirements

### Hardware Specifications

* **Processor**: Dual-core 2.0 GHz or faster is required.
* **Memory**: 4 GB RAM minimum (8 GB is preferred).
* **Disk Space**: Minimum 20 GB of free disk space.

### Supported Software

* **Operating Systems**:

  * Windows 10 / Windows 11
  * Most recent macOS versions
  * Popular Linux distributions like Ubuntu and Debian

* **VPN Protocols Supported**:

  * IPsec
  * SSL/TLS

### Additional Notes

* Make sure systems are updated with current security patches.
* A valid and active license on the Security Gateway is required for Remote Access VPN to function.

## Core Features

* **Encrypted Data Transfer**: All information sent between client and gateway is fully encrypted.
* **Multi-Factor Authentication (MFA)**: Works with certificates, token passwords, and other verification tools.
* **Clientless Access Option**: Supports web-based remote sessions without full software installation.
* **Built-In Endpoint Protection**: Provides firewall capabilities and ensures endpoint compliance.
* **Visitor Mode**: Routes VPN traffic over HTTP or HTTPS, which helps users connect in restricted networks.

## Setup and Configuration

### Managing User Groups

1. In SmartConsole, go to `Security Policies > Access Control`.
2. Place the necessary users into the `Remote Access VPN Community` under `Participant User Groups`.

### Setting Access Permissions

1. Create rules to control what remote users can access.
2. Associate allowed services or apps with the VPN Community.
3. Save changes and apply the new policy configuration.

### Assigning Custom VPN Domains

If a Security Gateway belongs to more than one VPN Community, you can assign a separate VPN Domain for each.

#### Steps:

1. Open `Network Management > VPN Domain`.
2. Link a specific domain to the appropriate VPN Community.
3. Customize the domain settings according to internal policy.

## Troubleshooting Guide

### Common Issues and Resolutions

* **Unexpected Disconnections**:

  * Check the network connection and review VPN gateway configuration.

* **Authentication or Login Errors**:

  * Verify login credentials and confirm authentication settings are correct.

* **Incorrect Routing**:

  * Review Office Mode settings and confirm correct IP pool assignment.

### Handy Diagnostic Commands

* On Linux:

  ```bash
  sudo strongswan restart
  journalctl -u strongswan
  ```

* On Windows:

  * Use the built-in Check Point diagnostics tool to gather logs and perform analysis.

## Advanced Configurations

### Managing Encryption Policies

* Configure encryption algorithms and settings at either the global level or per user.
* Supports flexible options for selecting ciphers and ensuring message integrity.

### Enabling DynamicID

* Turn on SMS- or email-based one-time passcode authentication for improved security.

### Setting Up Split Tunneling

* Implement split tunneling to restrict VPN routing to only certain traffic, while allowing general internet access through the local connection.

### Glossary

* **IPsec**: A suite of standards that protect IP traffic through encryption and authentication.
* **IKE (Internet Key Exchange)**: The protocol used to negotiate secure connections within IPsec.
* **VPN Domain**: A group of internal networks managed by a VPN Gateway, enabling secure remote access.
