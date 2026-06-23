# Technical Walkthrough

Each section explains the concept first in technical terms and then in plain language.

## 1. Subnetting

### Technical explanation

Fixed-Length Subnet Masking divides a larger network into equal-sized subnets. The corrected design allocates nine `/24` networks from `10.0.0.0/20`. Each `/24` provides 254 normally usable host addresses.

The WAN links use `/30` subnets, which provide two usable addresses and are efficient for point-to-point router connections.

### Plain-English explanation

Subnetting divides one large pool of addresses into smaller labelled areas. Every department receives its own area, while each router link only receives the two addresses it needs.

## 2. VLANs

### Technical explanation

A VLAN creates an independent Layer 2 broadcast domain. Switch access ports are assigned to one VLAN, while the trunk to the router carries multiple VLANs using IEEE 802.1Q tags.

### Plain-English explanation

VLANs build invisible walls inside the switch. HR, IT and Finance can share the same hardware without all behaving like one open network.

## 3. Router-on-a-Stick

### Technical explanation

Router-on-a-stick uses subinterfaces on one physical router interface. Each subinterface is assigned an 802.1Q VLAN tag and an IP address that becomes the default gateway for that VLAN.

### Plain-English explanation

One cable connects the switch and router, but labelled virtual lanes allow the router to serve several departments separately.

## 4. Default Gateway

### Technical explanation

A host sends traffic to its default gateway when the destination is outside its local IP subnet.

### Plain-English explanation

The gateway is the exit door a computer uses to reach another department or country.

## 5. RIPv2

### Technical explanation

RIPv2 is a distance-vector routing protocol that uses hop count as its metric and carries subnet-mask information. `no auto-summary` prevents classful summarisation.

### Plain-English explanation

The routers share directions with each other. RIP is simple and suitable for a small teaching network, although larger organisations usually prefer OSPF.

## 6. Port Security

### Technical explanation

Port security limits which MAC addresses may send traffic through a switch access port. Sticky learning records the first observed source MAC as secure.

Violation modes:

- Protect: drops unauthorised frames silently
- Restrict: drops frames and records the violation
- Shutdown: error-disables the interface

### Plain-English explanation

The switch remembers the expected device. If something else connects, it can quietly block it, record the attempt or close the port.

## 7. ICMP and Ping

### Technical explanation

Ping sends ICMP Echo Requests and waits for Echo Replies. A successful response verifies bidirectional Layer 3 reachability, but it does not prove that every application or firewall policy works.

### Plain-English explanation

Ping asks another device, “Can you hear me?” A reply confirms that the network path works in both directions.

## 8. Routing Table

### Technical explanation

The routing table contains connected, local and dynamically learned routes. RIP-learned entries appear with the code `R`.

### Plain-English explanation

The routing table is a router’s list of destinations and the next direction to take.

## 9. Device Hardening

### Technical explanation

The reconstructed configuration uses descriptive hostnames, privileged secrets, SSH-only VTY access, login controls, disabled DNS lookup and shutdown of unused ports.

### Plain-English explanation

These settings make the equipment easier to manage and reduce casual or accidental access.

## 10. SSH Remote Management

### Technical explanation

SSH provides encrypted remote command-line access to routers and switches. The reference configuration follows this chain:

1. The device needs a reachable IP address.
2. The hostname and domain name provide the identity used for RSA-key generation.
3. RSA keys enable encrypted SSH communication.
4. A local username and secret provide authentication.
5. VTY lines use `login local` and accept SSH only.

A Layer 2 switch also needs a management VLAN interface and a default gateway so administrators on another network can reach it. This educational design uses each site's IT VLAN for switch management. A dedicated management VLAN would be a stronger future improvement.

The RSA-key command is included as a comment because the key must be generated on the actual Packet Tracer device after the hostname and domain are configured.

### Plain-English explanation

SSH lets an administrator manage a router or switch remotely without sending commands and passwords as readable text. The device is given an address, an identity, encryption keys and a login account. It is then told to accept encrypted SSH connections instead of insecure Telnet connections.

A simple way to remember the chain is:

> Reach it, identify it, encrypt it, authenticate it and permit it.
