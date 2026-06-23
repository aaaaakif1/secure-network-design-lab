# Security Controls

## VLAN Separation

VLANs reduce unnecessary broadcast traffic and create boundaries between departments. VLANs alone are not a complete security policy; access-control lists or firewalls are needed to decide which inter-VLAN traffic is allowed.

## Port Security

![Port-security comparison](../assets/diagrams/port-security-modes.png)

The reconstructed design applies:

- UK HR port: protect
- India HR port: restrict
- USA HR port: shutdown

![Illustrative port-security output](../assets/illustrative-outputs/port-security-example.png)

## Management Security

The reference configurations include:

- Descriptive hostnames
- `enable secret`
- Local login controls
- SSH-only VTY access
- MOTD warning banner
- Disabled DNS lookup
- Shutdown of unused switch ports

Credentials are redacted in the public files.

## Firewall and VPN Recommendation

![Firewall and VPN design](../assets/diagrams/firewall-and-vpn-design.png)

A realistic deployment would place a higher-capacity next-generation firewall at the UK headquarters and smaller branch firewalls at India and USA. Site-to-site VPNs would encrypt traffic crossing untrusted networks.
