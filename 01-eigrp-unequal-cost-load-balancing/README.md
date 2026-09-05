# EIGRP Unequal-Cost Load Balancing

## Objective

I configured EIGRP on four routers and used two paths with different costs from R1 to the 192.168.4.0/24 LAN.

## Topology

![Topology](topology.png)

## Concepts

- EIGRP AS 100
- Unequal-cost load balancing
- Loopbacks and passive interfaces

## Configuration Highlights

- I set `variance 2` on R1 to allow both paths into the routing table.
- I advertised the loopback networks and R4's LAN while keeping those interfaces passive.
- I disabled automatic summarization on all four routers.

## Verification

I checked EIGRP neighbors, protocol settings, and R1's routing table.

- The path through 10.0.12.2 had a metric of 28672.
- The path through 10.0.13.2 had a metric of 30976.
- PC1 could ping R1's loopback at 1.1.1.1 with no packet loss.

## Result

R1 installed both paths to 192.168.4.0/24, even though their costs were different. The ping test also confirmed connectivity from PC1 to R1's loopback.
