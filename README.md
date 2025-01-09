# Multiarea OSPF Configuration with IPv4 & IPv6

## Contents

1. [**Purpose**](#purpose)
2. [**Background**](#background)
3. [**Topology**](#topology)
     1. [**IPv4 Topology**](#ipv4-topology)
     2. [**IPv6 Topology**](#ipv6-topology)
4. [**Address Table**](#address-table)
5. [**Device Overview**](#device-overview)
6. [**ICMPv4 Ping Across Network**](#icmpv4-ping-across-network)
7. [**ICMPv6 Ping Across Network**](#icmpv6-ping-across-network)
8. [**IPv4 Routing Table**](#ipv4-topology)
9. [**IPv6 Routing Table**](#ipv6-topology)

## Purpose

## Background

This is section is background info on key concept/parts of the configuration. It is directed an audience that knows some networking, but their knowledge is limited.

## Topology

These are the topologies for both IPv4 and IPv6, each link is labeled with the network number and subnet mask of the link. Then each interface is labeled with the 4th octet of the usable IP address within the subnet of that link.\
Additionally, the PCs can have any IP that is within the subnet of the link that they are on. **DHCP is not setup**.

### <center>IPv4 Topology</center>

### <center>IPv6 Topology</center>

## Address Table

| Device Name | Interface | IPv6 Address | IPv4 Address | Subnet Mask   |
|:------------|:--------- |:------------ |:------------ |:------------- |
| R1          | G0/0/0    | 1:20::1/64   | 10.0.20.1    | 255.255.255.0 |
| R1          | G0/0/1    | 1::1/64      | 10.0.0.1     | 255.255.255.0 |
| R2          | G0/0/0    | 1::2/64      | 10.0.0.2     | 255.255.255.0 |
| R2          | G0/0/1    | 2::1/64      | 192.168.0.1  | 255.255.255.0 |
| R3          | G0/0/0    | 2::2/64      | 192.168.0.2  | 255.255.255.0 |
| R3          | G0/0/1    | 1:1::1/64    | 10.0.1.1     | 255.255.255.0 |
| R4          | G0/0/0    | 1:2::2/64    | 10.0.2.2     | 255.255.255.0 |
| R4          | G0/0/1    | 2:1::1/64    | 192.168.1.1  | 255.255.255.0 |
| R5          | G0/0/0    | 2:1::2/64    | 192.168.1.2  | 255.255.255.0 |
| R5          | G0/0/1    | 1:3::1/64    | 10.0.3.1     | 255.255.255.0 |
| R6          | G0/0/0    | 1:3::2/64    | 10.0.3.2     | 255.255.255.0 |
| R6          | G0/0/1    | 1:30::1/64   | 10.0.30.1    | 255.255.255.0 |
| R7          | G0/0/0    | 1:1::2/64    | 10.0.1.2     | 255.255.255.0 |
| R7          | G0/0/1    | 1:2::1/64    | 10.0.2.1     | 255.255.255.0 |


## Device Overview

This Topology Consists of...

- Six 4321 routers running Cisco IOS XE Software, Version 16.9 Universal K9

## ICMPv4 Ping Across Network

## ICMPv6 Ping Across Network

## R1 IPv4 Routing Table
```
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2
       i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
       ia - IS-IS inter area, * - candidate default, U - per-user static route
       o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
       a - application route
       + - replicated route, % - next hop override, p - overrides from PfR

Gateway of last resort is not set

      3.0.0.0/32 is subnetted, 1 subnets
O E2     3.3.3.3 [110/10] via 10.0.0.2, 01:14:33, GigabitEthernet0/0/1
      4.0.0.0/32 is subnetted, 1 subnets
O E2     4.4.4.4 [110/10] via 10.0.0.2, 01:12:41, GigabitEthernet0/0/1
      10.0.0.0/8 is variably subnetted, 8 subnets, 2 masks
C        10.0.0.0/24 is directly connected, GigabitEthernet0/0/1
L        10.0.0.1/32 is directly connected, GigabitEthernet0/0/1
O E2     10.0.1.0/24 [110/10] via 10.0.0.2, 01:14:33, GigabitEthernet0/0/1
O E2     10.0.2.0/24 [110/10] via 10.0.0.2, 01:12:41, GigabitEthernet0/0/1
O E2     10.0.3.0/24 [110/10] via 10.0.0.2, 01:12:41, GigabitEthernet0/0/1
C        10.0.20.0/24 is directly connected, GigabitEthernet0/0/0
L        10.0.20.1/32 is directly connected, GigabitEthernet0/0/0
O E2     10.0.30.0/24 [110/10] via 10.0.0.2, 01:12:41, GigabitEthernet0/0/1
O     192.168.0.0/24 [110/2] via 10.0.0.2, 01:14:37, GigabitEthernet0/0/1
O E2  192.168.1.0/24 [110/10] via 10.0.0.2, 01:12:41, GigabitEthernet0/0/1

```

## R1 IPv6 Routing Table
```
IPv6 Routing Table - default - 13 entries
Codes: C - Connected, L - Local, S - Static, U - Per-user Static route
       B - BGP, R - RIP, I1 - ISIS L1, I2 - ISIS L2
       IA - ISIS interarea, IS - ISIS summary, D - EIGRP, EX - EIGRP external
       ND - ND Default, NDp - ND Prefix, DCE - Destination, NDr - Redirect
       O - OSPF Intra, OI - OSPF Inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
       ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2, a - Application
C   1::/64 [0/0]
     via GigabitEthernet0/0/1, directly connected
L   1::1/128 [0/0]
     via GigabitEthernet0/0/1, receive
OE2 1:1::/64 [110/10]
     via FE80::CE7F:76FF:FE6A:B5E0, GigabitEthernet0/0/1
OE2 1:2::/64 [110/10]
     via FE80::CE7F:76FF:FE6A:B5E0, GigabitEthernet0/0/1
OE2 1:3::/64 [110/10]
     via FE80::CE7F:76FF:FE6A:B5E0, GigabitEthernet0/0/1
C   1:20::/64 [0/0]
     via GigabitEthernet0/0/0, directly connected
L   1:20::1/128 [0/0]
     via GigabitEthernet0/0/0, receive
OE2 1:30::/64 [110/10]
     via FE80::CE7F:76FF:FE6A:B5E0, GigabitEthernet0/0/1
O   2::/64 [110/2]
     via FE80::CE7F:76FF:FE6A:B5E0, GigabitEthernet0/0/1
OE2 2:1::/64 [110/10]
     via FE80::CE7F:76FF:FE6A:B5E0, GigabitEthernet0/0/1
OE2 100:3::3/128 [110/10]
     via FE80::CE7F:76FF:FE6A:B5E0, GigabitEthernet0/0/1
OE2 100:4::4/128 [110/10]
     via FE80::CE7F:76FF:FE6A:B5E0, GigabitEthernet0/0/1
L   FF00::/8 [0/0]
     via Null0, receive
```
