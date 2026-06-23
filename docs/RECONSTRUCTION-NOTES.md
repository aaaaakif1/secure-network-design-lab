# Reconstruction Notes

The original coursework had useful technical content but mixed several incompatible pieces of visual evidence. This portfolio version fixes the structure without pretending the old screenshots represented one consistent build.

## Corrections

1. **One addressing scheme**
   - Corrected design: `10.0.1.0/24` to `10.0.9.0/24`
   - WAN links: `172.16.0.0/30` and `172.16.0.4/30`

2. **Router-on-a-stick is explicitly defined**
   - The original report described VLANs and routing but did not show the inter-VLAN method clearly.

3. **RIP statement corrected**
   - The USA router uses `network 172.16.0.0`, not `network 172.16.0.4`.

4. **Generic screenshots are no longer presented as evidence**
   - Generated images are labelled illustrative.
   - Authentic Packet Tracer screenshots require the actual `.pkt` build.

5. **Plaintext example passwords removed**
   - Public configuration templates contain `<REDACTED>` placeholders.

6. **Security claims are more precise**
   - `service password-encryption` is weak reversible obfuscation, not strong encryption.
   - VLANs provide segmentation but require ACLs or firewalls for detailed policy enforcement.

## Scope

This repository is a portfolio reconstruction based on the completed university project. It is not presented as the original assessed submission.
