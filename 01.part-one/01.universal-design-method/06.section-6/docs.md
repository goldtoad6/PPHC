---
menu: 实战：虚拟电商平台“静山”
title: 高并发实战：虚拟电商平台“静山”
taxonomy:
    category: docs
---

静山是我国境内最矮的山，它仅仅高出地面 0.6 米，如图 1-4 所示，但却是一座货真价实的山，用来给我们的虚拟电商平台命名正合适。

![](/media/16889116095787.jpg)
<center>图 1-4 静山实拍图</center>

假设我们拥有一个电商平台，名为静山，它以 APP 的形式对外服务，没有 Web 端，官网域名为 `js.com`。静山平台的初始架构如图 1-5 所示。

![](/media/16888969420441.jpg)
<center>图 1-5 静山平台初始架构</center>

### 静态资源云服务化

作为一个 2023 年的电商平台，静态资源必须全部云服务化，这已经是最新的业界技术标准了。为了实现云服务化，可以采取以下步骤：

1. 存储层：使用对象存储服务（如阿里云 OSS 和亚马逊 S3）来存储静态资源。
2. 前端接入层：通过 CDN（内容分发网络）域名直接对接对象存储服务，实现静态资源的无缝访问和负载均衡。CDN 将静态资源副本分布在全国各个节点，让每个地方的用户都能用最快的速度访问静态资源。
3. 减轻后端压力：将静态资源独立出后端系统，减轻后端系统的负担，提高系统的性能和可伸缩性。后端系统可专注于业务逻辑处理，而无需关心静态资源的管理和访问。

### GraphQL 协议

根据笔者过去五年的实践，GraphQL 是最佳的客户端数据交互协议，它能在很大程度上避免后端工程师的低级错误。笔者十分推荐大家尝试这个新技术。

#### GraphQL 是最佳的客户端数据交互协议

GraphQL 是一种用于客户端与服务器之间进行数据交互的协议，它是一种灵活且高效的数据传递方式。相比于传统的 RESTful API，GraphQL 具有更好的可扩展性和性能优势。使用 GraphQL，前端可以直接请求所需的数据，而无需经过繁琐的中间件或模板引擎处理。这种直接的数据获取方式可以减少网络传输的数据量，提高应用的性能。

#### 避免后端工程师的低级错误

通过使用 GraphQL，后端工程师可以将更多的注意力集中在业务逻辑上，而不是处理底层的数据请求细节。GraphQL 提供了一种类型安全的方式来定义数据模型和查询，减少了潜在的数据一致性问题和错误。这使得后端工程师可以更加专注于编写高质量的代码，减少低级错误的发生。

#### GraphQL 可以被看作是一种编程语言的“Java 化”

从软件工程的角度来看，GraphQL 可以被看作是一种编程语言的“Java 化”。Java 是一种广泛使用的编程语言，以其严谨的语法规则和强大的生态系统而闻名。类似地，GraphQL 通过增加繁复而严密的规范，使得编程语言可以更加健壮和可靠。这有助于提高软件的整体质量，并减少了由于低级错误而导致的问题。

#### 可以只依靠架构师的个人能力来保证软件质量

通过引入 GraphQL，相当于给灵活的编程语言（如 PHP、Go）引入了规范的严格，软件的质量可以得到保证。通过使用这些规范严格的语言和框架，架构师可以更好地管理和控制整个软件开发过程，从而保证软件的质量水平。同时，这也使得非高级工程师能够更容易地写出可用的代码，提高了整个团队的开发效率。

### 数据库分开部署

如果预算有限，我们可以选择基于云主机自建数据库并自己进行数据备份。这种方式的优点是灵活性高，可以根据自己的需求进行定制和优化。但是缺点也很明显，那就是需要投入大量的时间和精力进行运维，而且数据备份和恢复的过程也可能会遇到各种问题。

如果预算充足，我们强烈建议大家直接使用云服务商提供的云数据库服务。云数据库是云服务商最核心的“软件服务”之一，也是最具用户价值和用户粘性的云产品。它的优点在于稳定性高，安全性好，而且可以随着业务的发展进行弹性扩展。此外，云数据库还可以提供丰富的数据分析和处理功能，对于我们未来的高并发系统建设非常重要。

需要注意的是，虽然云主机、对象存储、CDN 都很容易迁移，但云数据库几乎无法在云服务商之间迁移，在选择云数据库服务时，我们需要考虑到这一点。

### 云数据库的价值

云数据库绝不只是“不用自己做运维”那么简单，它拥有很多额外价值：

首先，云数据库拥有完善的数据备份和恢复机制。这不仅可以保证数据库的安全，还能提供自建数据库无法做到的“闪回到任意时刻”的能力。在实际的业务运行过程中，这种需求其实是相当常见的。例如，可能需要从过去的某个时间点恢复数据来进行数据分析或者修复错误。云数据库通常提供了多种备份和恢复策略，可以满足不同的需求。

其次，云数据库的性能更高。一旦你对数据库的需求超过了 1000QPS，自建数据库就很难支撑了。开源的 MySQL 在低配机器上性能很强，但是即便给它 32 核 64GB 内存，它的性能也不会好到哪里去。如果招聘研发团队自建数据库集群，那就太复杂了，小公司完全不值得，每年投入数百万成本养活运维和开发小团队，可能数据库集群还是会经常宕机。相比之下，云数据库可以提供高性能的数据库服务，可以轻松应对高并发的访问请求。

最后，云数据库具有极佳的弹性。大部分互联网业务的流量都拥有显著的波动性，除了每天每周的业务高峰期之外，电商行业每年还有超级大促日。所以，数据库的弹性非常重要，按需付费可以节约大量金钱。云数据库可以根据实际的业务需求进行资源的动态调整，避免了资源的浪费。