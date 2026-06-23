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
- Local administrator accounts
- SSH version 2 instead of Telnet
- RSA-key generation instructions
- SSH-only VTY access
- MOTD warning banner
- Disabled DNS lookup
- Shutdown of unused switch ports
- Management VLAN interfaces on the switches

SSH provides encrypted remote command-line access. Local usernames authenticate administrators, RSA keys protect the session and the VTY lines accept SSH only.

The Layer 2 switches use their site IT VLANs for management:

- UK switch: VLAN 20, `10.0.2.2`
- India switch: VLAN 21, `10.0.5.2`
- USA switch: VLAN 22, `10.0.8.2`

A dedicated management VLAN would be preferable in a larger or production network.

All credentials remain redacted in the public repository. The SSH commands are reference templates and are not claimed as tested Packet Tracer evidence.

## Firewall and VPN Recommendation

![Firewall and VPN design](../assets/diagrams/firewall-and-vpn-design.png)

A realistic deployment would place a higher-capacity next-generation firewall at the UK headquarters and smaller branch firewalls at India and USA. Site-to-site VPNs would encrypt traffic crossing untrusted networks.
