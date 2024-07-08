---
title: "YANG Data Models for Transport TE FGNM Extension Model"
abbrev: "TE FGNM YANG"
category: std

docname: draft-yu-ccamp-te-fgnm-yang-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Routing"
workgroup: "Common Control and Measurement Plane"
keyword:
 - next generation
 - unicorn
 - sparkling distributed ledger
venue:
  group: "Common Control and Measurement Plane"
  type: "Working Group"
  mail: "ccamp@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/ccamp/"
  github: "YuChaode/draft-yu-ccamp-te-fgnm-yang"
  latest: "https://YuChaode.github.io/draft-yu-ccamp-te-fgnm-yang/draft-yu-ccamp-te-fgnm-yang.html"

author:
  -
    name: Chaode Yu
    org: Huawei Technologies
    email: yuchaode@huawei.com
  -
    name: Xing Zhao
    org: CAICT
    email: zhaoxing@caict.ac.cn
  -
    name: Yanxia Tan
    org: China Unicom
    email: tanyx11@chinaunicom.cn
  -
    name: Nigel Davis
    org: Ciena
    email: ndavis@ciena.com
  -
    name: Daniel King
    org: Old Dog Consulting
    email: daniel@olddog.co.uk

contributor:
  -
    name: Zhoulong Liu
    org: Huawei Technologies
    email: liuzhoulong@huawei.com
  -
    name: Italo Busi
    org: Huawei Technologies
    email: Italo.Busi@huawei.com
  -
    name: Aihua Guo
    org: Futurewei Technologies
    email: aihuaguo.ietf@gmail.com

normative:

informative:

  TMF-814:
    title: MTNM Solution Set (IDL) R4.5
    author:
      org: TM Forum (TMF)
    date:  2014
    seriesinfo: TMF-814
    target: https://www.tmforum.org/resources/interface/tmf814-mtnm-solution-set-idl-version-r4-5/


  ONF_TR-547:
    title: TAPI v2.1.3 Reference Implementation Agreement
    author:
      org: Open Networking Foundation (ONF)
    date:  July 2020
    seriesinfo: ONF TR-547 TAPI RIA v1.0
    target: https://opennetworking.org/wp-content/uploads/2020/08/TR-547-TAPI-v2.1.3-Reference-Implementation-Agreement-1.pdf

  ITU-T_G.805:
    title: Generic functional architecture of transport networks
    author:
      org: International Telecommunication Union
    date:  March 2000
    seriesinfo: ITU-T Recommendation G.805
    target: https://www.itu.int/rec/T-REC-G.805-200003-I/en


  ITU-T_G.808:
    title: Terms and definitions for network protection and restoration
    author:
      org: International Telecommunication Union
    date:  November 2016
    seriesinfo: ITU-T Recommendation G.808
    target: https://www.itu.int/rec/T-REC-G.808-201611-I/en

  ITU-T_G.874:
    title: Management aspects of optical transport network elements
    author:
      org: International Telecommunication Union
    date:  October 2020
    seriesinfo: ITU-T Recommendation G.874
    target: https://www.itu.int/rec/T-REC-G.874-202010-I/en

  ITU-T_G.875:
    title: Optical transport network%3AProtocol-neutral management information model for the network element view
    author:
      org: International Telecommunication Union
    date:  June 2020
    seriesinfo: ITU-T Recommendation G.875
    target: https://www.itu.int/rec/T-REC-G.875-202006-I/en

--- abstract

This document defines two extension YANG data models augmenting to TE topology and TE tunnel modules, based on the FGNM (Fine-Grain Network Management) requirements in transport networks.

--- middle

# Introduction

{{!RFC8795}} defines a YANG data module for technology generic, and it is augmented by some other technology specific data modules, e.g. OTN topology data model in {{?I-D.draft-ietf-ccamp-otn-topo-yang}}.

{{?I-D.draft-ietf-teas-yang-te}} defines a YANG data model for the provisioning and management of Traffic Engineering (TE) tunnels, Label Switched Paths (LSPs), and interfaces. Similarly, it could be also augmented by some other technology specific data modules to implement a specific layer of TE tunnel.


According to {{?I-D.draft-ietf-ccamp-transport-nbi-app-statement}}, it is good to used the current TE data model system to manage an abstracted network topology. In {{?I-D.draft-gstk-ccamp-actn-optical-transport-mgmt}}, it is called Abstracted Control (AC) approach.

In {{?I-D.draft-gstk-ccamp-actn-optical-transport-mgmt}}, it also raised another management approach, which is called Fine-Grain Network Management (FGNM). FGNM is aimed to provide traditional FCAPS capabilities.

{{ITU-T_G.805}} describes transport network from the viewpoint of the information transfer capability, provides a generic functional architecture which is also implementation independent. This recommendation is the implementation basis of most of the vendors' or operators' systems.

To provide traditional FCAPS functionalities, we need to align with the modelling of traditional approach, which is suggested to be {{TMF-814}}. Therefore, some more TMF attributes would be introduced. To avoid introducing non-backward-compatible (NBC) changes, we would like to provide some extension YANG data models, based on the current model architecture.

Some extensions is generic for all network layers would be defined in the FGNM extension models, including generic TE topology FGNM extension and generic TE tunnel FGNM extension. The layer specific FGNM extension should be found in some other YANG data modules.


## Terminology and Notations

Note: to be added on demand.

## Requirements Notation

{::boilerplate bcp14}

## Tree Diagram

A simplified graphical representation of the data model is used in this document.
The meaning of the symbols in this diagram is defined in {{!RFC8340}}.

## Prefix in Data Node Names

  In this document, names of data nodes and other data model objects
  are prefixed using the standard prefix associated with the
  corresponding YANG imported modules, as showned in the following table.

| Prefix | Yang Module                     | Reference     |
| ------ | ------------------------------- | ------------- |
| nw     | ietf-network                    | {{!RFC8345}}  |
| nt     | ietf-network-topology           | {{!RFC8345}}  |
| tet    | ietf-te-topology                | {{!RFC8795}}  |
| yang   | ietf-yang-types                 | {{!RFC6991}}  |
| inet   | ietf-inet-types                 | {{!RFC6991}}  |
|te      | ietf-te                         | RFCYYYY |
| te-types| ietf-te-types                  | {{!RFC8776}}  |
| tet-fgnm-ext| ietf-te-topology-fgnm-ext  | RFC XXXX      |
| te-fgnm-ext| ietf-te-fgnm-ext            | RFC XXXX      |
| te-types-fgnm-ext| ietf-te-types-fgnm-ext| RFC XXXX      |
{: #tab-prefixes title="Prefixes and corresponding YANG modules"}

RFC Editor Note:
Please replace XXXX with the RFC number assigned to this document.
Please replace YYYY with the RFC number assigned to the TE tunnel draft.
Please remove this note.

# Mapping of ACTN modelling objects with TMF objects

{{ITU-T_G.805}} describes the network as a transport network from the viewpoint of the information transfer capability. More specifically, the functional and structural architecture of transport networks are described independently of networking technology. It also defines various types of reference points, such as the Access Point (AP), Connection Point (CP), and Trail Connection Point (TCP), and the processing between reference points, which is called adaptation. A transport entity that transmits information such as trails and connections between reference points. For the details, we can refer to descriptions in chapter 3 of {{ITU-T_G.805}} and Figure 1 to Figure 3.

One disadvantage of {{ITU-T_G.805}} is it is too complicated. So TMF simplifies the modelling system of {{ITU-T_G.805}}. The adaptation is changed to be the capabilities of reference points. The reference points is so that changed to some other terminologies, e.g. PTP and FTP etc. This simplification still can be mapped to {{ITU-T_G.805}}. So that a lot of vendors and operators choose TMF modelling in their system.

Based on the TMF modelling, CORBA/XML interface was defined to provide FCAPS interfaces. These interfaces were widely used in the operators' network.

The transport ACTN is also initially designed to simplify network configurations. To have a unified modelling with IP technology, many new modelling terms of TE were introduced and build up a new modelling system. Theoretically, these new modelling objects should be a part of, or can be mapped to the reference points or adaptation defined by {{ITU-T_G.805}}. However, in the existing IETF documents, there is not sufficient details can be found.

If the transport ACTN interface wants to support the complete FCAPS capability, there could be two approaches. The first approach is the ACTN interface build up a new alarm/performance monitoring mechanism,  based on its abstract control modelling. Just like what have been done in {{ITU-T_G.874}} and {{ITU-T_G.875}}.

The second approach is reusing the traditional alarm/performance monitoring mechanism, so that the ACTN modelling needs to be mapped to the traditional modelling.

Currently, there is not sufficient theoretical support for the first approach, and there is not such a attempt is tried in IETF. For the second approach, one of the advantage is it can inherit the functions integrated before. So that there would not be two much efforts need to pay for the new integration.

In this document, we would like to follow the second approach. Table 2 provides a mapping between the ACTN objects and TMF objects.

| ACTN Object  | TMF Object                  |
| -------------| ----------------------------|
| Network      | NA                          |
| Node         | Management Element          |
| Link         | Topology Link               |
| TP           | PTP                         |
| TTP          | CTP/FTP                     |
| Tunnel       | SNC/XC                      |
| NE           | Management Element          |
| component    | equipment holder/equipment  |
| Client signal| NA                          |
| Ethernet Client signal| NA                 |
| NA            | Protection Group           |
| NA            | Equipment Protection Group |
{: #tab-mapping title="Mapping of ACTN objects with TMF objects"}

The ONF TAPI also defines a new set of terms, which are different from the definitions of the {{ITU-T_G.805}}. But it provides the mapping of TAPI objects to ITU-T objects in Figure 3-2 of {{ONF_TR-547}}. In the appendix of this document, we also compare the ACTN object modelling and TAPI object modelling, which can be used as a reference for a possible integration of these two interfaces in a same MDSC.

# Model relationship

The current ACTN topology models for transport technology follows the relationship as bellow:

~~~~ ascii-art
          +----------------------+
          |  network topology    |
          +----------------------+
                      ^
                      |augmenting
                      |
          +----------------------+
          |     TE topology      |
          +----------------------+
             ^      ^       ^
             |  augmenting  |
  augmenting |      |       |
   +--------------+ |       |
   | ETH topology | |       |
   +--------------+ |       |
                    |       |augmenting
          +--------------+  |
          | OTN topology |  |
          +--------------+  |
                            |
              +--------------+
              | WDM topology |
              +--------------+

~~~~
{: #fig-actn-topology title="Relationship of ACTN topology"}

TE topology model was aimed to define common attributes for all the technologies.  OTN topology and WDM topology, etc., they are all augmenting TE topology model to provide layer-specific extensions.

Although most of the objects in ACTN and TMF can be mapped to each other, the parameters of the objects cannot be completely matched. In other words, the current ACTN object needs to be extended with some properties to support the full functionality of a traditional object.

But in the traditional transport standards there is not such a saying of  TE-related modelling. If we want to extend the current IETF data models to have full modelling of traditional approach, which is called FGNM extension by us, we suggest to define the common attributes for all the technologies in a TE topology FGNM extension model.

For layer-specific FGNM extensions could reference existing way and define in a separated layer-specific FGNM extension document. So in the FGNM approach, the ACTN topology architecture will be extended to be:

~~~~ ascii-art
       +----------------------+
       |  network topology    |
       +----------------------+
                   ^
                   |
                   |
       +----------------------+           +----------------------+
       |     TE topology      |<----------|   TE FGNM Extension  |
       +----------------------+           +----------------------+
          ^      ^       ^                     ^      ^       ^
          |      |       |                     |      |       |
          |      |       |                     |      |       |
+--------------+ |       |         +----------------+ |       |
| ETH topology | |       |         | ETH FGNM EXT   | |       |
+--------------+ |       |         +----------------+ |       |
                 |       |                            |       |
       +--------------+  |                +--------------+    |
       | OTN topology |  |                | OTN FGNM EXT |    |
       +--------------+  |                +--------------+    |
                         |                                    |
           +--------------+                     +--------------+
           | WDM topology |                     | WDM FGNM EXT |
           +--------------+                     +--------------+
~~~~
{: #fig-actn-fgnm-topology title="Relationship of FGNM ACTN topology"}

It is also same for the TE tunnel architecture. The whole architecture after FGNM tunnel extensions will be:

~~~~ ascii-art
   +----------------------+           +----------------------+
   |      TE Tunnel       |<----------|   TE FGNM Extension  |
   +----------------------+           +----------------------+
        ^      ^       ^                   ^      ^       ^
        |      |       |                   |      |       |
        |      |       |                   |      |       |
+------------+ |       |       +----------------+ |       |
| ETH Tunnel | |       |       | ETH FGNM EXT   | |       |
+------------+ |       |       +----------------+ |       |
               |       |                          |       |
     +--------------+  |              +--------------+    |
     | OTN Tunnel   |  |              | OTN FGNM EXT |    |
     +--------------+  |              +--------------+    |
                       |                                  |
           +--------------+                 +--------------+
           | WDM Tunnel   |                 | WDM FGNM EXT |
           +--------------+                 +--------------+
~~~~
{: #fig-actn-fgnm-tunnel title="Relationship of FGNM ACTN tunnel"}

# FGNM Topology

For the some objects, although it is defined in IETF, but the way of abstraction is not so implementation friendly,  especially for TTP.

## FGNM extension for TE topology
(To be added)

## The modelling and usage of TTP

According to the description of {{!RFC8795}}, TTP is an element of a TE topology representing one or several potential transport service termination points, (i.e., service client adaptation points, such as a WDM/OCh transponder).

In the ITU-T standard, such an adaptation point can be the termination point of an end-to-end connection, or the source or sink point of the intermediate cross-connection. A physical port can generate a lot of logical objects. For example, a 100G line port can function as 80 lower-order ODU0 adaptation points, 40 ODU1 adaptation points, or even the adaptation point of an OCh tunnel. Considering  the data volume in large-scale network, it is not wise to expose all these points. Because that most of them are potentially existing, they are probably not used at the end.

In the document of TE topology, it is not indicated  whether the TTPs should be provided at day 0 or not. And it is also hard to find the correlation with the physical port.

In this document, we suggest not to provide the potential TTPs but the existing TTPs who have been used by connections at any time. If the client want to retrieve these potential TTPs, a single RPC can help to do so. This RPC should return the existing and potential TTPs at the same time.

The key of TTP is tunnel-tp-id which is a binary type. For the potential TTPs, it is no need to allocate a tunnel-tp-id for them. But the server can provide a name for these TTPs, this name should follow the pattern defined by TMF. When the client want to reference a potential TTP, it can reference the name of this TTP, and then the server will allocated a tunnel-tp-id for it after the connection created. And this TTP is no more than a potential TTP but an existing TTP, it should appear in the TTP list of topology.

~~~~ ascii-art
rpcs:
   +---x query-ttp-by-tps
      +--ro input
      |  +--ro tp-list* [tp-id]
      |     +--ro tp-id    leafref
      +--ro output
         +--ro result?        enumeration
         +--ro result-list* [tp-id]
            +--ro tp-id      leafref
            +--ro ttp-list*
               +--ro tunnel-tp-id?   leafref
               +--ro ttp-name?       string
               +--ro using-status?   enumeration
~~~~

# FGNM Extensions for TE Tunnel

## Modelling of Point to Multi-Points and Multi-Points to Multi-Points TE Tunnel

The current TE tunnel model only supports point-to-point scenario. Therefore, only one source and sink structure is defined on the tunnel node. In the transport technology, there are point-to-multipoint scenarios and multipoint-to-multipoint connection scenarios. For example, multicast service.

We suggest to extend the current TE tunnel model to support the multi-point scenario. Considering the TTPs was not generate before the tunnel created, the client can reference by the TTP by name.

## Restoration

### Lock of restoration

In some maintenance scenarios, people may need to freeze the restoration capability of a TE tunnel. For example, after obtaining the customers' consent, the carrier can choose not to restore services during the TE tunnel cutover. This prevents unstable services flapping caused by repeated fiber cuts during the cutover. The unstable services flapping would also affects existing services.

Section 3.2.8.11 in {{ITU-T_G.808}} mentions the freezing operation of protection and rerouting switching. Therefore, compared with traditional path management, the current TE tunnel model also needs to add freezing capability to the  protection and restoration structure.

### Lock of restoration reversion

For some cutover scenario, services may be rerouted to a new trail before the cutover operation. During the cutover, the fiber may be frequently plug in and plug out due to commissioning. To make sure that the new route will not go back to the original route and if the tunnel is restoration reversion, there would be a requirement the freeze the restoration reversion function. This is also a functionality defined by ITU-T and it's missing in the current TE tunnel.

### Scheduling of reversion time

Maintenance job usually is taken place in a fixed time window, for example at night when people are not using the network frequently as daytime. So that there will not be impact as large as operating at daytime if the maintenance job is failed. Operator can choose to revert the services to the original path at night, so that the restoration reversion would not have big impact on the network.

### Priority of restoration

In some operator, they configure different restoration priority to different tunnels or services. When multiple services need to be restored at a same time, high-priority services preferentially occupy resources, and low-priority services can be rerouted only after the rerouting of high-priority services is complete.

### YANG for restoration extension

~~~~ ascii-art
augment /te:te/te:tunnels/te:tunnel/te:restoration:
   +--rw restoration-lock?             boolean
   +--rw restoration-reversion-lock?   boolean
   +--rw scheduled-reversion-time?     yang:date-and-time
   +--rw restoration-priority?         enumeration
~~~~

## TTP hop
The current TE tunnel data model can support to specify explicit node/LTP included/excluded. However, for finer grain object, such as TTP, it is not supported to specify.

For example, in the scenario where lower-order and higher-order ODUk tunnel are both existing, sometimes multiple lower-order ODUk tunnels need to multiplex a higher-order ODUk tunnel. The client can specify the higher-order ODUk tunnel's TTP to be included in the lower-order ODUk tunnel's creation request. If the lower-order ODUk doesn't need to multiplex a higher-order ODUk tunnel, the client can specify the higher-order ODUk tunnel's TTP to be excluded in the lower-order ODUk tunnel's creation request.

There can be two ways to specify this TTP. This higher-order ODUk TTP can be existing in the topology if it has been occupied by a higher-order ODUk tunnel. Then in the TTP hop, the client can specify the ttp-id of this TTP. This TTP can also be nonexisting in the topology or idle for tunnel creation. And then then client can specify the name of TTP in the creation request.

~~~~ ascii-art
augment /te:te/te:tunnels/te:tunnel/te:primary-paths/te:primary-path
        /te:explicit-route-objects-always
        /te:route-object-include-exclude/te:type:
   +--:(ttp-hop)
      +--rw ttp-hop
         +--rw node-id?    nw:node-id
         +--rw (id-or-name)?
            +--:(id)
            |  +--rw ttp-id?     binary
            +--:(name)
               +--rw ttp-name?   string
augment /te:te/te:tunnels/te:tunnel/te:secondary-paths
        /te:secondary-path/te:explicit-route-objects-always
        /te:route-object-include-exclude/te:type:
   +--:(ttp-hop)
      +--rw ttp-hop
         +--rw node-id?    nw:node-id
         +--rw (id-or-name)?
            +--:(id)
            |  +--rw ttp-id?     binary
            +--:(name)
               +--rw ttp-name?   string
augment /te:te/te:tunnels/te:tunnel/te:primary-paths/te:primary-path
        /te:primary-reverse-path/te:explicit-route-objects-always
        /te:route-object-include-exclude/te:type:
   +--:(ttp-hop)
      +--rw ttp-hop
         +--rw node-id?    nw:node-id
         +--rw (id-or-name)?
            +--:(id)
            |  +--rw ttp-id?     binary
            +--:(name)
               +--rw ttp-name?   string
augment /te:te/te:tunnels/te:tunnel/te:secondary-reverse-paths
        /te:secondary-reverse-path/te:explicit-route-objects-always
        /te:route-object-include-exclude/te:type:
   +--:(ttp-hop)
      +--rw ttp-hop
         +--rw node-id?    nw:node-id
         +--rw (id-or-name)?
            +--:(id)
            |  +--rw ttp-id?     binary
            +--:(name)
               +--rw ttp-name?   string
~~~~


#  Tree Diagram

## FGNM Extension for TE Topology

{{fig-tet-fgnm-tree}} below shows the tree diagram of the YANG data model defined in module "ietf-te-topology-fgnm-ext".

~~~~ ascii-art
{::include ./yang/ietf-te-topology-fgnm-ext.tree}
~~~~
{: #fig-tet-fgnm-tree title="Tree of TE Topology FGNM Extension"
artwork-name="ietf-te-topology-fgnm-ext.tree"}


## FGNM Extension for TE Tunnel

{{fig-te-fgnm-tree}} below shows the tree diagram of the YANG data model defined in module "ietf-te-fgnm-ext".

~~~~ ascii-art
{::include ./yang/ietf-te-fgnm-ext.tree}
~~~~
{: #fig-te-fgnm-tree title="Tree of TE Tunnel FGNM Extension"
artwork-name="ietf-te-fgnm-ext.tree"}

# YANG Data Model

## FGNM Extensin for TE Topology

~~~~ yang
{::include ./yang/ietf-te-topology-fgnm-ext.yang}
~~~~
{: #fig-tet-fgnm-yang title="TE Topology FGNM Extension YANG module"
sourcecode-markers="true" sourcecode-name="ietf-te-topology-fgnm-ext@2024-07-08.yang"}

## FGNM Extensin for TE Tunnel
~~~~ yang
{::include ./yang/ietf-te-fgnm-ext.yang}
~~~~
{: #fig-te-fgnm-yang title="TE Tunnel FGNM Extension YANG module"
sourcecode-markers="true" sourcecode-name="ietf-te-fgnm-ext@2024-07-08.yang"}


# Manageability Considerations

  \<Add any manageability considerations>

# Security Considerations

  \<Add any security considerations>

# IANA Considerations

  \<Add any IANA considerations>

--- back

# Appendix

## Mapping Between ACTN & TMF & TAPI Modelling

| ACTN Object  | TMF Object                  |TAPI Object         |
| -------------| ----------------------------|--------------------|
| Network      | NA                          |topology            |
| Node         | Management Element          |node                |
| Link         | Topology Link               |link                |
| TP           | PTP                         |SIP/NEP             |
| TTP          | CTP/FTP                     |CEP                 |
| Tunnel       | SNC/XC                      |connection          |
| NE           | Management Element          |device              |
| component    | equipment holder/equipment  |equipment/holder    |
| Client signal| NA                          |connectivity service|
| Ethernet Client signal| NA                 |connectivity service|
| NA            | Protection Group           |NA                  |
| NA            | Equipment Protection Group |NA                  |
{: #tab-mapping2 title="Mapping of ACTN & TMF & TAPI Modelling"}

{: numbered="false"}

# Acknowledgments

This document was prepared using kramdown.
