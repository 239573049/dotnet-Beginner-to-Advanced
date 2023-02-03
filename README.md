# .NET 入门到高级路线

1. [c# 基础语法](#csharp基础语法)
2. [.NET Core 基础知识](#.NETCore基础知识)
    - [ASP.NET Core 基础知识概述](#ASP.NETCore基础知识概述)
    - [Blazor](#Blazor)
3. [ORM](#ORM)
    - [freesql](#freesql)
    - [Entity Framework Core](#EntityFrameworkCore)
    - [Dapper](#Dapper)
    - [SqlSugar](#SqlSugar)
4. [关系型数据库](#数据库) 
    - [SQL Server](#SQLServer)
    - [MySql](#MySql)
    - [PostgreSQL](#PostgreSQL)
5. [中间件](#中间件)
    - [mongodb](#mongodb)
    - [Redis](#Redis)
    - [Rabbitmq](#Rabbitmq)
    - [ActiveMQ](#ActiveMQ)
    - [Skywalking](#Skywalking)
    - [Consul](#Consul)
    - [Kafka](#Kafka)
    - [Dapr](#Dapr)
6. [运维](#运维)
   	- [Docker](#Docker)
   	- [Docker Compose](#DockerCompose)
   	- [Drone](#Drone)
   	- [CI/CD](#CI/CD)
7. [微服务](#微服务)

8. [应用框架](#应用框架)
    - [ABP](#ABP)

## CSharp基础语法

微软官方教程地址 ：[C# 文档 - 入门、教程、参考。 | Microsoft Learn](https://learn.microsoft.com/zh-cn/dotnet/csharp/)

b站视频：

[刘铁猛《C#语言入门详解》全集_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV13b411b7Ht/?spm_id_from=333.337.search-card.all.click)

[C#语言入门详解](https://www.bilibili.com/video/BV1wx411K7rb/?spm_id_from=333.337.search-card.all.click)

## .NET Core 基础知识

微软官方教程地址：[使用 ASP.NET Core 创建 Web API | Microsoft Learn](https://learn.microsoft.com/zh-cn/aspnet/core/web-api/?WT.mc_id=dotnet-35129-website&view=aspnetcore-7.0)

[.NET 6教程，.Net Core 2022视频教程，杨中科主讲_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1pK41137He/?spm_id_from=333.337.search-card.all.click)

### ASP.NETCore基础知识概述

- [依赖关系注入](https://learn.microsoft.com/zh-cn/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-7.0)
- [中间件](https://learn.microsoft.com/zh-cn/aspnet/core/fundamentals/middleware/?view=aspnetcore-7.0)
- [配置](https://learn.microsoft.com/zh-cn/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0)
- [选项](https://learn.microsoft.com/zh-cn/aspnet/core/fundamentals/configuration/options?view=aspnetcore-7.0)
- [环境](https://learn.microsoft.com/zh-cn/aspnet/core/fundamentals/environments?view=aspnetcore-7.0)
- [Logging](https://learn.microsoft.com/zh-cn/aspnet/core/fundamentals/logging/?view=aspnetcore-7.0)
- [路由](https://learn.microsoft.com/zh-cn/aspnet/core/fundamentals/routing?view=aspnetcore-7.0)
- [处理错误](https://learn.microsoft.com/zh-cn/aspnet/core/fundamentals/error-handling?view=aspnetcore-7.0)
- [静态文件](https://learn.microsoft.com/zh-cn/aspnet/core/fundamentals/static-files?view=aspnetcore-7.0)

### Blazor

Blazor 是一个使用 Blazor 生成交互式客户端 Web UI 的框架：

- 使用 [C#](https://learn.microsoft.com/zh-cn/dotnet/csharp/) 代替 [JavaScript](https://www.javascript.com/) 来创建信息丰富的交互式 UI。
- 共享使用 .NET 编写的服务器端和客户端应用逻辑。
- 将 UI 呈现为 HTML 和 CSS，以支持众多浏览器，其中包括移动浏览器。
- 与新式托管平台（如 [Docker](https://learn.microsoft.com/zh-cn/dotnet/standard/microservices-architecture/container-docker-introduction/index)）集成。
- 使用 .NET 和 Blazor 生成混合桌面和移动应用。

使用 .NET 进行客户端 Web 开发可提供以下优势：

- 使用 C# 代替 JavaScript 来编写代码。
- 利用现有的 [.NET 库](https://learn.microsoft.com/zh-cn/dotnet/standard/class-libraries)生态系统。
- 在服务器和客户端之间共享应用逻辑。
- 受益于 .NET 的性能、可靠性和安全性。
- 使用开发环境（例如 [Visual Studio](https://visualstudio.microsoft.com/) 或 [Visual Studio Code](https://code.visualstudio.com/)）保持 Windows、Linux 或 macOS 上的工作效率。
- 以一组稳定、功能丰富且易用的通用语言、框架和工具为基础来进行生成。
- 

 [Blazor 微软官方文档](https://learn.microsoft.com/zh-cn/aspnet/core/blazor/?view=aspnetcore-7.0)

 [Blazor 基础教程](https://www.bilibili.com/video/BV1bD4y1n7qj/?share_source=copy_web&vd_source=8c159155ad844a1144bbf369d0046094)

Blazor UI框架推荐
- [Masa Blazor](https://www.masastack.com/blazor)(作者推荐)
- [Bootstrap Blazor](https://www.blazor.zone/)
- [Ant Design Blazor](https://ant-design-blazor.gitee.io/zh-CN/docs/introduce)
- [MatBlazor](https://www.matblazor.com/)
- [Radzen Blazor](https://blazor.radzen.com/)


## ORM

ORM简介 
        对象关系映射（Object Relational Mapping，简称ORM）模式是一种为了解决面向对象与关系数据库存在的互不匹配的现象的技术。简单的说，ORM是通过使用描述对象和数据库之间映射的元数据，将程序中的对象自动持久化到关系数据库中。那么，到底如何实现持久化呢？一种简单的方案是采用硬编码方式，为每一种可能的数据库访问操作提供单独的方法。 
        这种方案存在以下不足： 
        1.持久化层缺乏弹性。一旦出现业务需求的变更，就必须修改持久化层的接口 
        2.持久化层同时与域模型与关系数据库模型绑定，不管域模型还是关系数据库模型发生变化，毒药修改持久化曾的相关程序代码，增加了软件的维护难度。 
　　· 简单：以最基本的形式建模数据。 
　　· 传达性：数据库结构被任何人都能理解的语言文档化。 
　　· 精确性：基于数据模型创建正确标准化了的结构。 

### [freesql](https://freesql.net/)

是一款功能强大的对象关系映射（O/RM）组件，支持 .NET Core 2.1+、.NET Framework 4.0+ 以及 Xamarin✨

### [EntityFrameworkCore](https://learn.microsoft.com/zh-cn/ef/core/)
Entity Framework (EF) Core 是轻量化、可扩展、开源和跨平台版的常用 Entity Framework 数据访问技术。(作者推荐efcore是由微软官方维护)

### [Dapper](https://dapper-tutorial.net/dapper)
Dapper是由Stack Overflow背后的团队创建的micro-ORM。Dapper 是 .NET 的简单对象映射器，在速度方面拥有 Micro ORM 之王的称号，几乎与使用原始 ADO.NET 数据读取器一样快。ORM是一个对象关系映射器，负责数据库和编程语言之间的映射。

### [SqlSugar](https://www.donet5.com/Home/Doc)
SqlSugar 是一款 老牌 .NET 开源ORM框架，由果糖大数据科技团队维护和更新

## 关系型数据库

### [SQLServer](https://www.microsoft.com/zh-cn/sql-server/sql-server-downloads)

SQL Server是由Microsoft开发和推广的**关系数据库管理系统(DBMS)**；
SQL Server使用方便，伸缩性好与相关软件集成程度高；
SQL Server 数据库引擎为关系型数据和结构化数据提供了更安全可靠的存储功能。

### [MySql](https://www.mysql.com/)

MySQL 是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好的 RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

### [PostgreSQL](https://www.postgresql.org/)

PgSQL PostgreSQL 的历史简介. 现在被称为 PostgreSQL 的对象- 关系型数据库管理系统 （有一段时间被称为 Postgres95）是从伯克利写的 POSTGRES 软件包发展而来的。. 经过十几年的发展， PostgreSQL 是世界上可以获得的最先进的 开放源码 的 数据库系统 ， 它提供了多版本并行控制，支持几乎所有 SQL 构件 （包括 子查询 ， 事务 和用户定义类型和函数）， 并且可以获得非常广阔范围的（开发）语言绑定（包括 C，C++，Java，perl，tcl，和 python）

## 中间件

中间件是介于应用系统和系统软件之间的一类软件，它使用系统软件所提供的基础服务（功能），衔接网络上应用系统的各个部分或不同的应用，能够达到资源共享、功能共享的目的。它并没有很严格的定义，但是普遍接受IDC的定义：中间件是一种独立的系统软件服务程序，分布式应用软件借助这种软件在不同的技术之间共享资源，中间件位于客户机服务器的操作系统之上，管理计算资源和网络通信。从这个意义上可以用一个等式来表示中间件：中间件=平台+通信，这也就限定了只有用于分布式系统中才能叫中间件，同时也把它与支撑软件和实用软件区分开来。

### [mongodb](https://www.mongodb.com/)

MongoDB 是一个基于分布式文件存储的数据库。由 C++ 语言编写。旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。

MongoDB 是一个介于关系数据库和非关系数据库之间的产品，是非关系数据库当中功能最丰富，最像关系数据库的。

### [Redis](https://redis.io/)

REmote DIctionary Server(Redis) 是一个由 Salvatore Sanfilippo 写的 key-value 存储系统，是跨平台的非关系型数据库。

Redis 是一个开源的使用 ANSI C 语言编写、遵守 BSD 协议、支持网络、可基于内存、分布式、可选持久性的键值对(Key-Value)存储数据库，并提供多种语言的 API。

Redis 通常被称为数据结构服务器，因为值（value）可以是字符串(String)、哈希(Hash)、列表(list)、集合(sets)和有序集合(sorted sets)等类型。

### [Rabbitmq](https://www.rabbitmq.com/)
RabbitMQ是实现了高级消息队列协议（AMQP）的开源消息代理软件（亦称面向消息的中间件）。RabbitMQ服务器是用Erlang语言编写的，而集群和故障转移是构建在开放电信平台框架上的。所有主要的编程语言均有与代理接口通讯的客户端库。

### [ActiveMQ](https://activemq.apache.org/)

Apache ActiveMQ是Apache软件基金会所研发的开放源代码消息中间件；由于ActiveMQ是一个纯Java程序，因此只需要操作系统支持Java虚拟机，ActiveMQ便可执行。

### [Skywalking](https://skywalking.apache.org/)

用于分布式系统的应用程序性能监视工具，特别为微服务、云原生和基于容器(Kubernetes)架构设计。

### [Consul](https://www.consul.io/)

Consul是微服务架构中，解决服务发现、配置中心的分布式中间件。
Consul是HashiCorp公司推出的开源工具，Consul由Go语言开发，部署起来非常容易，只需要极少的可执行程序和配置文件，具有绿色、轻量级的特点。Consul是分布式的、高可用的、 可横向扩展的用于实现分布式系统的服务发现与配置。

  - 服务发现（Service Discovery）：Consul提供了通过DNS或者HTTP接口的方式来注册服务和发现服务。一些外部的服务通过Consul很容易的找到它所依赖的服务。
  - 健康检查（Health Checking）：Consul的Client可以提供任意数量的健康检查，既可以与给定的服务相关联(“webserver是否返回200 OK”)，也可以与本地节点相关联(“内存利用率是否低于90%”)。操作员可以使用这些信息来监视集群的健康状况，服务发现组件可以使用这些信息将流量从不健康的主机路由出去。
  - Key/Value存储：应用程序可以根据自己的需要使用Consul提供的Key/Value存储。 Consul提供了简单易用的HTTP接口，结合其他工具可以实现动态配置、功能标记、领袖选举等等功能。
  - 安全服务通信：Consul可以为服务生成和分发TLS证书，以建立相互的TLS连接。意图可用于定义允许哪些服务通信。服务分割可以很容易地进行管理，其目的是可以实时更改的，而不是使用复杂的网络拓扑和静态防火墙规则。
  - 多数据中心：Consul支持开箱即用的多数据中心. 这意味着用户不需要担心需要建立额外的抽象层让业务扩展到多个区域。

### [Kafka](https://kafka.apache.org/)

Kafka是一种高吞吐量的分布式发布订阅消息系统，它可以处理消费者规模的网站中的所有动作流数据。 这种动作（网页浏览，搜索和其他用户的行动）是在现代网络上的许多社会功能的一个关键因素。 这些数据通常是由于吞吐量的要求而通过处理日志和日志聚合来解决。 对于像Hadoop的一样的日志数据和离线分析系统，但又要求实时处理的限制，这是一个可行的解决方案。Kafka的目的是通过Hadoop的并行加载机制来统一线上和离线的消息处理，也是为了通过集群机来提供实时的消费。

### [Dapr](https://dapr.io/)
Dapr 是一个可移植的、事件驱动的运行时，它使任何开发人员能够轻松构建出弹性的、无状态和有状态的应用程序，并可运行在云平台或边缘计算中，它同时也支持多种编程语言和开发框架。

[微软Dapr简介](https://learn.microsoft.com/zh-cn/dotnet/architecture/dapr-for-net-developers/foreword)

## 运维

### [Docker](https://docs.docker.com/get-docker/)

Docker 是一个开源的应用容器引擎，基于 Go 语言 并遵从 Apache2.0 协议开源。

Docker 可以让开发者打包他们的应用以及依赖包到一个轻量级、可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。

容器是完全使用沙箱机制，相互之间不会有任何接口（类似 iPhone 的 app）,更重要的是容器性能开销极低。

### [DockerCompose](https://docs.docker.com/compose/)

Compose 是用于定义和运行多容器 Docker 应用程序的工具。通过 Compose，您可以使用 YML 文件来配置应用程序需要的所有服务。然后，使用一个命令，就可以从 YML 文件配置中创建并启动所有服务。

### [Drone](https://www.drone.io/)

Drone是为繁忙的开发团队提供的自助持续集成平台。

### CI/CD
CI 持续集成（Continuous Integration）
协同开发是目前主流的开发方式，也就是多位开发人员可以同时处理同一个应用的不同模块或者功能。

但是，如果企业计划在同一天，将所有开发分支代码集成在一起，最终可能会花费很多时间和进行很多重复劳动，费事费力。因为代码冲突是难以避免的。

如果开发人员本地的环境和线上不一致的话，那么这个问题就更加复杂了。

持续集成（CI）可以帮助开发者更加方便地将代码更改合并到主分支。

一旦开发人员将改动的代码合并到主分支，系统就会通过自动构建应用，并运行不同级别的自动化测试（通常是单元测试和集成测试）来验证这些更改，确保这些更改没有对应用造成破坏。

如果自动化测试发现新代码和现有代码之间存在冲突，CI 可以更加轻松地快速修复这些错误。

CD 持续交付（Continuous Delivery）
CI 在完成了构建、单元测试和集成测试这些自动化流程后，持续交付可以自动把已验证的代码发布到企业自己的存储库。

持续交付旨在建立一个可随时将开发环境的功能部署到生产环境的代码库。

在持续交付过程中，每个步骤都涉及到了测试自动化和代码发布自动化。

在流程结束时，运维团队可以快速、轻松地将应用部署到生产环境中。

CD 持续部署（Continuous Deployment）
对于一个完整、成熟的 CI/CD 管道来说，最后的阶段是持续部署。

它是作为持续交付的延伸，持续部署可以自动将应用发布到生产环境。

实际上，持续部署意味着开发人员对应用的改动，在编写完成后的几分钟内就能及时生效（前提是它通过了自动化测试）。这更加便于运营团队持续接收和整合用户反馈。

总而言之，所有这些 CI/CD 的关联步骤，都极大地降低了应用的部署风险。

不过，由于还需要编写自动化测试以适应 CI/CD 管道中的各种测试和发布阶段，因此前期工作量还是很大的。

## 微服务

一种软件开发技术- 面向服务的体系结构（SOA）架构样式的一种变体，它提倡将单一应用程序划分成一组小的服务，服务之间互相协调、互相配合，为用户提供最终价值。每个服务运行在其独立的进程中，服务与服务间采用轻量级的通信机制互相沟通（通常是基于HTTP的RESTful API）。每个服务都围绕着具体业务进行构建，并且能够独立地部署到生产环境、类生产环境等。另外，应尽量避免统一的、集中式的服务管理机制，对具体的一个服务而言，应根据上下文，选择合适的语言、工具对其进行构建。

[.NET 应用程序体系结构文档](https://learn.microsoft.com/zh-cn/dotnet/architecture/)

[.NET 微服务。适用于容器化](https://learn.microsoft.com/zh-cn/dotnet/architecture/microservices/)

[使用 DDD 和 CQRS 模式降低微服务中的业务复杂性](https://learn.microsoft.com/zh-cn/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)

## 应用框架

### [ABP](https://abp.io/)

ABP是一个开源且文档友好的应用程序框架。ABP不仅仅是一个框架，它还提供了一个最徍实践的基于领域驱动设计(DDD)的体系结构模型，可以支持.net framework和.net core两种技术流派。

**ABP 框架特点**

- 依赖注入，这个部分使用 Castle windsor （依赖注入容器）来实现依赖注入，这个也是我们经常使用IOC来处理的方式；
- Repository仓储模式，已实现了Entity Framework、NHibernate、MangoDB、内存数据库等，仓储模式可以快速实现对数据接口的调用；
- 身份验证与授权管理，可以使用声明特性的方式对用户是否登录，或者接口的权限进行验证，可以通过一个很细粒度的方式，对各个接口的调用权限进行设置；
- 数据有效性验证，ABP自动对接口的输入参数对象进行非空判断，并且可以根据属性的申请信息对属性的有效性进行校验；
- 审计日志记录，也就是记录我们对每个接口的调用记录，以及对记录的创建、修改、删除人员进行记录等处理；
- Unit Of Work工作单元模式，为应用层和仓储层的方法自动实现数据库事务，默认所有应用服务层的接口，都是以工作单元方式运行，即使它们调用了不同的存储对象处理，都是处于一个事务的逻辑里面；
- 异常处理，ABP框架提供了一整套比较完善的流程处理操作，可以很方便的对异常进行进行记录和传递；
- 日志记录，我么可以利用Log4Net进行常规的日志记录，方便我们跟踪程序处理信息和错误信息；
- 多语言/本地化支持，ABP框架对多语言的处理也是比较友好的，提供了对XML、JSON语言信息的配置处理；
- Auto Mapping自动映射，这个是ABP的很重要的对象隔离概念，通过使用AutoMaper来实现域对象和DTO对象的属性映射，可以隔离两者的逻辑关系，但是又能轻松实现属性信息的赋值；
- 动态Web API层，利用这个动态处理，可以把Application Service 直接发布为Web API层，而不需要在累赘的为每个业务对象手工创建一个Web API的控制器，非常方便；
- 动态JavaScript的AJax代理处理，可以自动创建Javascript 的代理层来更方便使用Web Api，这个在Web层使用。

**ABP 框架特别的功能**

- 多租户支持（每个租户的数据自动隔离，业务模块开发者不需要在保存和查询数据时写相应代码；
- 软删除支持（继承相应的基类或实现相应接口，会自动实现软删除）
- 系统设置存取管理（系统级、租户级、用户级，作用范围自动管理）
- EventBus实现领域事件(Domain Events)
- 模块以及模块的依赖关系实现插件化的模块处理等等

![image](https://user-images.githubusercontent.com/61819790/216491752-d93b6867-f693-495e-8b2a-e30b1e89e3d2.png)

### [masastack](https://docs.masastack.com/framework/concepts/overview)

全新的.NET现代应用开发，提供分布式应用运行时–基于Dapr云原生最佳实践，能够快速实现分布式、微服务、DDD，SaaS等现代应用开发

![image](https://user-images.githubusercontent.com/61819790/216491618-c9f3823c-eb2e-4270-923b-3c9030dd2bc2.png)


## 结尾

欢迎大佬继续补充，壮大dotnet生态！

来着token的分享

技术交流群：737776595
