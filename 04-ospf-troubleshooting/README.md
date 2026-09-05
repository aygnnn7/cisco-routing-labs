# OSPF Troubleshooting and LSDB Analysis

## Objective

I fixed routing problems in an existing OSPF Area 0 network. My goal was to restore connectivity from both LANs and check the OSPF database.

## Topology

![Topology](topology.png)

## Concepts

- OSPF neighbors and network types
- Passive interfaces
- Default routes
- OSPF link-state database (LSDB)

## Configuration Highlights

- I added IP addresses and OSPF to the R1-R2 serial link and set the DCE clock rate on R1.
- I corrected the OSPF network-type mismatch between R3 and R4.
- I restored OSPF neighbor connections on the shared 192.168.245.0/29 network.
- R3 advertised its LAN with a passive LAN interface.
- R5 shared its static default route toward the ISP through OSPF.

## Verification

I checked neighbors, interfaces, routing tables, and the LSDB. The database contained Type 1, Type 2, and Type 5 LSAs.

I tested both LANs with ping and traceroute to 8.8.8.8.

## Result

The router neighbors reached FULL state, and the default route appeared as an OSPF E2 route. Both PCs could reach 8.8.8.8.
