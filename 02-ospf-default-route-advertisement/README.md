# OSPF Default Route Advertisement

## Objective

Configure a single-area OSPF network in Area 0 and use R1 as an Autonomous System Boundary Router (ASBR) to advertise a default route toward the ISP into the OSPF domain.

## Topology

![Topology](topology.png)

## Concepts

- OSPF Area 0
- IPv4 routing
- /30 point-to-point networks
- Loopback interfaces
- Passive interfaces
- OSPF ASBR
- Default route advertisement
- OSPF external Type 2 routes
- Equal-cost OSPF paths

## Configuration Highlights

- OSPF process 1 was configured across R1, R2, R3, and R4 in Area 0.
- Router loopbacks were advertised in OSPF and configured as passive interfaces.
- R4's LAN interface was advertised while remaining passive.
- R1 used a static default route toward the ISP and originated it into OSPF with `default-information originate`.
- R2 and R3 learned the default route from R1 as an OSPF external Type 2 route.
- R4 installed two equal-cost OSPF external default paths through R2 and R3.

## Verification

The lab was verified using:

- `show ip ospf neighbor`
- `show ip protocols`
- `show ip route`
- End-to-end ICMP connectivity from PC1 to the router loopbacks

All required OSPF neighbor relationships reached FULL state, the expected OSPF routes were installed, and PC1 successfully reached remote loopback interfaces.

## Result

R1 successfully operated as the ASBR for the OSPF domain and advertised a default route toward the ISP. R2 and R3 installed a single OSPF E2 default route, while R4 installed two equal-cost OSPF E2 default paths.
