---
layout: post
title: Passed CCIE SPv4.1
date: 2017-07-22
tags: CCIE
---

On the 12th of July 2017, I passed the CCIE SPv4.1 lab exam in Brussels on my first attempt. This is my second CCIE after Routing & Switching that I passed in April 2015. I haven't seen any success story for the new SPv4.1 revision which is most probably due to the general lack of CCIE SP workbooks, the low number of people even attempting the lab, and the fact that this revision change has been introduced on the 21st of June 2017. Therefore, I decided to write this blog post where I will explain my preparation for the CCIE SP.

I started with my CCIE SP preparation shortly after I passed the CCIE RS. The new SPv4 revision was just around the corner and I was eager to see the workbooks and full scale labs that INE would come up with. Back then I was still a Full Access INE member with roughly 12 more months of subscription on my account. As we all know, INE did not live up to our expectations with respect to the CCIE SPv4 material which was basically a minor revision of CCIE SPv3 materials and was not covering the topics in much detail. In early 2016, with only a few months of INE Full Access left on my account, I decided that I would study on my own and not keep waiting for INE to come up with new workbooks or full scale labs.

I will not make a difference between written - and lab exam preparation because even for the written I spent a lot of time on the CLI to understand new features. What follows is a potential approach for lab candidates to prepare for the CCIE SPv4.1 lab:

## Blueprint Readiness

Download the CCIE SPv4.1 Unified Blueprint from <https://learningcontent.cisco.com/cln_storage/text/cln/marketing/exam-topics/400-201-ccie-sp-unified.pdf>, go through each topic and do a self assessment. Depending on your background, or previous certifications (such as CCIE RS), you may have several blueprint items that you don't need to study again, or only do a quick refresh. Personally, I identified the following key topics that needed some serious preparation:

- **ISIS**
- **MPLS Traffic Engineering**
- **Multicast VPN**
- **QoS (MPLS QoS models, MPLS TE QoS)**
- **Carrier Ethernet**
- **L3VPN (Inter-AS, U-MPLS, CSC, Services)**
- **Overlay VPN**
- **System level HA**
- **Routing/Fast Convergence**
- **IPv6 in general**
- **Segment Routing**

Now that you know what you don't know it's time to create a study plan. You should refresh every single topic on the blueprint and spend additional time on topics that are new to you, or that you couldn't configure without looking up the Cisco Doc (except for MVPN).

## Study Buddy

From my experience having a study buddy is invaluable. I don't like large study groups because they tend to get messy, and the overhead to synchronize between all members is pretty big. I would recommend a dedicated group of 2-3 people that share the same study plan, take notes and synch on a regular base after each key topic from the blueprint. Ideally, you have a common Wiki, or similar, where all members share their notes.

## Virtual Lab

A virtual lab is mandatory for both CCIE RS/SP and should ideally fulfill the following requirements:

- **Packet Captures:** When configuring new features, or troubleshooting a problem, it is crucial to be able to have a look at the control - and data plane packets in your network. MPLS is a key topic from the blueprint so we need to fully understand our label stack on every hop along the path.
- **Large Scale:** Your server should be able to run 20+ devices in order to have a realistic lab feeling
- **Flexible:** Changing the topology should not take longer than 10min
- **L2 Segmentation:** L2VPN requires that both PE-CE links are in different L2 domains
- **Save Simulations:** This comes in handy when dealing with more advanced features like U-MPLS or CSC that require a lot of work to setup

Unfortunately, there is not a single approach which ticks off all those points: 

### ESXi

After the CCIE RS I continued my studies using the INE approach where we basically run our VMs on an ESXi server, connect all devices to a single L2 domain and then inter-connect devices using dot1q.

**Benefits:** Packet Captures, Large Scale

I would recommend this approach in the beginning of your CCIE studies where the topology will not change very often, and where we need to look at packet captures to fully understand a feature.

### Virtual Internet Routing Lab (VIRL)

During the last two months before my lab exam I moved away from ESXi to VIRL because it is much more flexible to create new full scale labs, change software versions, add new links and separate L2 domains. Unfortunately, I didn't try to capture packets but I believe this functionality exists as well.

**Benefits:** Large Scale, Flexible, L2 Segmentation, Save Simulations

I would recommend this approach for all candidates which are working on full scale labs to increase their speed.

## Lab, lab, lab

Now that you have created a study plan, found a study group and built a virtual lab, it's time to start labbing. How are we supposed to practice without a workbook? Follow the config guide!

Here is what I did usually:

1. Open the IOS XE - and IOS XR configuration guide for the feature that I want to practice
2. Read the config guide, extract all the configuration tasks and features that are listed for both IOS XE and IOS XR
3. Create sections for feature X, Y, Z on my Wiki Page and add subsections for IOS XE(IPv4+IPv6)/IOS XR(IPv4+IPv6)
4. Create a big topology which can be used to configure all subtasks of a certain feature
5. Start with the first feature, configure it, verify it, debug it, troubleshoot it and track all your steps under the section of your Wiki document

There is no feature parity between IOS XE and IOS XR but this doesn't mean that a feature is not part of the lab. Also, some features, like the data plane of L2VPN are not supported in IOS XR. Again, this doesn't mean that it cannot be tested in any of the three lab sections (Tshoot, Diag & Config).

Obviously, it was not always straight forward to configure a new feature because I did not properly understand a feature, my configuration was wrong, or the data plane of feature X was not supported. In this case I was usually looking at other learning resources that will be listed under "Recommended Reading" below.

## Bilingual

### IOS (XE) and IOS XR

The scope of the blueprint for SP candidates feels much smaller than for RS and it probably is. However, the fact that successful candidates need to master two different IOS versions - and syntaxes (IOS (XE) & IOS XR), adds a lot of complexity and additional preparation. Sure, the syntax between IOS XE and IOS XR is not that different and features are configured similarly, but it is important to remember the cases where they differ.

When going through the study guide I would recommend to always configure a feature between IOS XE and IOS XR. For example, when configuring Inter-AS, make sure that you have PE, P, ASBR and RR that run IOS XE and IOS XR. Ideally, you bring in some interoperability and not have IOS XE - and IOS XR islands.

### IPv4 and IPv6

Additionally, when configuring a feature, always activate IPv6! Configuring dual stack networks should feel natural to you before going to the lab.

## Recommended Reading

I recommend the following books for CCIE SP lab exam candidates:

- **IP Routing on Cisco IOS, IOS XE, and IOS XR:** Great resource for interoperability between IOS (XE) and IOS XR
- **Deploying Next Generation Multicast-Enabled Applications:** One of the few books on Multicast VPN that covers different vendors
- **MPLS in the SDN Era:** Probably the best book I have ever read on MPLS
- **MPLS Fundamentals:** Great book that I read previously for the CCIE RS

The following Cisco documentation guides are very helpful:

- [**IOS XR L2VPN Services and Features**](http://www.cisco.com/c/en/us/support/docs/routers/asr-9000-series-aggregation-services-routers/116453-technote-ios-xr-l2vpn-00.html)
- [**Configure mVPN Profiles Within Cisco IOS**](http://www.cisco.com/c/en/us/support/docs/ip/multicast/118985-configure-mcast-00.html)
- [**Configure mVPN Profiles Within Cisco IOS-XR**](http://www.cisco.com/c/en/us/support/docs/multiprotocol-label-switching-mpls/multiprotocol-label-switching-vpns-mpls-vpns/118983-configure-mpls-00.html)

Other resources:

- [**CCIE in 2 Months:**](http://ccie-in-2-months.blogspot.ch/) A bit dated but still helpful when looking up configurations
- [**Internetworking Blog by CCIE #45527:**](https://packetdrop85.wordpress.com) Great reference for MVPN/MPLS TE
- [**Cisco Live**](https://www.ciscolive.com)

Cisco Live presentations were my default gateway for technical information on topics that I was not familar with. I recommend the following excellent presentations:

- **BRKIPM-3017** - mVPN Deployment Models (2014 San Francisco)
- **BRKRST-3371** - Advances in BGP (2014 Melbourne)
- **BRKMPL-2102** - Designing MPLS-based IP VPNs (2017 Las Vegas) 
- **BRKRST-3020** - IP LFA (Loop-Free-Alternate): Architecture and Troubleshooting (2015 San Diego)
- **BRKMPL-2100** - Deploying MPLS Traffic Engineering (2017 Las Vegas)
- **BRKMPL-2101** - Deploying MPLS-based Layer 2 Virtual Private Networks (2015 San Diego)

## Speed is Key

Practicing with a dual screen setup, Putty and Notepad is important to have a similar environment like the real lab. Always look out for optimizations when configuring a certain feature:

- **BGP:** IOS XE: Peer-Groups/Templates - IOS XR: Neighbor-Groups
- **Route-Map/Route-Policy:** You should be able to write those rather quickly
- **Combine Features:** Time is limited in the lab so try to group tasks whenever feasible and touch a device once instead of 5 times
- **Master the documentation:** You don't have to know everything, but you need to know where to find it 
- **IOS XR CLI:** Try to replicate configuration as much as possible. For instance, configure one device, "root", "show", copy & paste and adapt the configuration
- **Regex is your friend:** Regular expressions can help you to filter unnecessary information, or extract only relevant configuration

## MVPN

MVPN was by far the hardest topic to crack for me. First of all, the learning curve is very steep and there is not much information available on the Internet. My strategy was to configure all profiles for PIM in the core, before moving on to MLDP Default MDT, MLDP Partitioned MDT, In-Band Signaling and P2MP-TE. Also, I didn't even bother to learn those profiles by heart. Instead, I was trying to understand the differences and benefits of each profile. The path to the mVPN configuration guide for IOS and IOS XR is very simple from the Support Page:

Technology -> IP -> IP Multicast -> IP Multicast -> Configuration Examples and Tech Notes

For each profile I would copy the configuration, adapt it to my case, and paste it.

## Full Scale Labs

One could program a full scale lab generator with the following ingredients:

1. Define two or more AS
2. Configure ISIS, OSPF in one of the AS
3. Configure LDP, MPLS TE, SR in one of the AS
4. Provide End-to-End reachability between the AS
5. Inter-AS Option A/B/C(with BGP LU)/C(with BGP<>IGP redistribution)
6. Add L2VPN/MVPN services on top
7. Add Inter-AS L2VPN/MVPN
etc

This post turned out to be much longer than expected so I will stop here. If you have additional questions regarding lab preparation or would be interested to see some configuration examples, feel free to contact me by email or leave a comment below.

**Please do not ask me to violate the Cisco NDA policy, as I will not share lab specific details.**




