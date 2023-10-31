---
title: 负载均衡发展史
taxonomy:
    category: docs
---

接下来，让我们一起回顾负载均衡技术的发展历程。

### F5 创业史

1996 年，华盛顿大学的几个学生共同创建了一家生产负载均衡设备的公司，并以美国人民的老朋友——飓风的最高等级 F5 作为品牌名，以表示他们的设备可以扛住最狂暴的网络流量。当时，互联网的规模每 100 天增长一倍，这也让 F5 在成立三年后迅速上市。2001 年，F5 公司在经历了互联网泡沫后，顺利地把设备卖进了银行等大型机构，因为 F5 比微软和甲骨文都更有前瞻性：他们的 iControl 系统可以提供 API，让大型机构自己开发软件来控制通过负载均衡设备的所有流量。

早在 2001 年，软件的威力就已经开始展现。

#### TMOS 软件平台

2003 年非典暴发，电子商务、网络点餐甚至是网络新闻都迎来了爆发式的增长。2004 年，F5 上市了新一代产品：包含 TMOS 软件平台的全套硬件设备，一次性解决了网络访问、数据中心同步访问、远程办公、应用防火墙等多种需求。此后，市场上 F5 公司的产品越来越具有统治力。

#### 迈向应用交付

2006 年以后，传统的 IP 层负载均衡技术开始向应用层发展，F5 等相关设备厂商也紧跟潮流开始推广“应用交付”的概念，开发了很多结合了负载均衡和应用网关的产品，这之后的十年，是传统负载均衡硬件厂商的最后荣光。

2019 年，F5 Networks 以 6.7 亿美金的价格收购了 Nginx，硬件厂商和软件厂商实现了一次梦幻联动，也侧面说明了我们确实已经迎来了软件定义网络的大时代。

#### 顺便提一句防火墙

实际上，在今天的企业网络架构中，专业的网关设备都已经消失，取而代之的是一个看起来不是网络设备的网络设备：防火墙。特别是具备应用识别能力的“下一代防火墙”（没错，就是这个中二的名字），更是将防火墙设备的价值推上了巅峰，并一次性让企业级路由器和中低端负载均衡器全部退出市场，这又是一个软件战胜硬件的故事。

> 一个小八卦，下一代防火墙行业的个中翘楚 Fortinet 公司，由两名出生于北京的清华大学老师的孩子于 2000 年在美国创办。

### 负载均衡一代目：硬件负载均衡

2002 年 2 月，戴尔为 PowerEdge 1650 服务器首次配备了千兆以太网。当时，负载均衡的主流实现是基于硬件的，也可以说是一种“软硬件一体化解决方案”。由于当时的服务器 CPU 单核性能较低，核心数也较少，网卡芯片技术远不如今天的 NPU 强大，因此想要通过运行在标准操作系统（Windows/Linux）内的软件来实现千兆软网关仍然是一个“前沿探索项目”。更不用说万兆负载均衡了：PowerEdge 1650 发布后四个月，万兆以太网的首个技术标准“IEEE 802.3ae 10 Gb/s 光纤以太网标准”才首次发布，距离万兆网卡在服务器端普及还有十多年的时间。

鲜为人知的是，千兆以太网的光纤标准于 1998 年发布，双绞线标准于 1999 年发布，而到了 2002 年，万兆以太网光纤标准已经发布。实际上，千兆以太网在消费端开始普及已经是 2010 年的事情了。

在 21 世纪的第一个十年里，最优秀的超千兆解决方案是利用二层网络的链路聚合协议，使用多个千兆口同时进行负载均衡，实现超过千兆的速度。而且当时能够提供数 G 带宽的负载均衡设备价格昂贵，动辄上百万，对于有需求的终端客户来说是个巨大的负担。然而，在那个移动通信基站都需要完全进口的时代，哪个中国人不是背负着巨大的负担呢？

这些网络硬件厂商实际上也是软件厂商，只不过它们选择将自己的软件安装在这些黑色的铁盒子里出售，这样的产品质量更稳定，更重要的是：这样更贵。相比于购买一个看起来可以随意复制盗版又虚无缥缈的软件，人类社会落后的官僚体系更容易接受购买昂贵的实物。具体的技术分析请继续阅读。

### 负载均衡二代目：软件负载均衡

近年来，随着云计算的兴起，硬件设备和 IT 基础设施发生了翻天覆地的变化。如今，硬件负载均衡逐渐退出舞台，取而代之的是云服务商们利用软件定义网络（SDN）技术构建的低成本高性能的新世界。

今天，一台总价 3 万元的通用 x86 服务器搭配 100G 以太网卡，使用基于 DPDK 开发的用户态应用程序在 Linux 上发送小包，轻松就能达到 100Gbps 的网卡带宽。（来自 Envoy 作者 Matt Klein 2017 年的一篇英文博客：[Introduction to modern network load balancing and proxying](https://blog.envoyproxy.io/introduction-to-modern-network-load-balancing-and-proxying-a57f6ff80236)）

![](https://qn.lvwenhan.com/2023-01-06-16730039147229.jpg)
<center>图 6-1 Brian Glas 关于软件定义网络的推文</center>

如图 6-1 的推文或许有些夸张，但这正是我们当下的现实：软件正在重新定义网络的一切。

### 价值百万的硬件设备

![](https://qn.lvwenhan.com/2022-12-28-16721666482414.jpg)
![](https://qn.lvwenhan.com/2022-12-29-16723036985096.jpg)
<center>图 6-2 F5 VPR-LTM-C2400-AC 的技术参数</center>

如图 6-2 所示是一台 F5 生产的售价百万的硬件负载均衡设备，仅凭一颗 4 核 8 线程的至强 x86 CPU，就实现了 40G 的四层负载均衡能力和 18G 的七层负载均衡（应用网关）能力。

这台设备内部有两个控制器和四个接口插槽，实现了“全双活”，即控制流量的“CPU 内存主板”和收发流量的“网络接口”都是双份。当任意一个资源意外宕机时，另一个备用资源可以无缝接替，实现无丢包的硬件级高可用性。同时，这台设备背后的电源适配器至少有四个，支持运行时热替换，甚至连风扇模组也是冗余、可热替换的。

接下来，我们将利用软件的力量，逐步在标准 x86 服务器上运行的标准 Linux 系统内，构建出一个与这台硬件负载均衡设备具有相同高可用性、且带宽可达 200G 的负载均衡集群。

让我们从交换机技术开始讲起。