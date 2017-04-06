# Docker实践教程

本文档旨在实验Docker1.13新特性和帮助大家了解docker集群的管理和使用。


## 环境配置

[Docker1.13环境配置](docs/docker_env.md)

[docker源码编译](docs/docker_compile.md)


## 网络管理

网络配置和管理是容器使用中的的一个重点和难点，对比我们之前使用的docker版本是1.11.1，docker1.13中网络模式跟之前的变动比较大，我们会花大力气讲解。

[如何创建docker network](docs/create_network.md)

[一步步教你创建一个自定义网络](docs/create_network_step_by_step.md)

[Rancher网络探讨和扁平网络实现](docs/rancher_network.md)

[swarm mode的路由网络](docs/swarm_mode_routing_mesh.md)

[docker扁平化网络插件Shrike（基于docker1.11）](https://github.com/TalkingData/shrike)

## 存储管理

[Docker存储插件](docs/docker_storage_plugin.md)

- [infinit](docs/infinit.md) 被docker公司收购的法国团队开发
- [convoy](docs/convoy.md) rancher开发的docker volume plugin
- [torus](docs/torus.md) **已废弃**
- [flocker](docs/flocker.md) ClusterHQ开发



## 日志管理

Docker提供了一系列[log drivers](https://docs.docker.com/engine/admin/logging/overview/)，如fluentd、journald、syslog等。

需要配置docker engine的启动参数。

[docker logging driver](docs/docker_logging_driver.md)

## 创建应用

官方文档：[Docker swarm sample app overview](https://docs.docker.com/engine/getstarted-voting-app/)

[基于docker1.13手把手教你创建swarm app](docs/create_swarm_app.md)

[swarm集群应用管理](docs/swarm_app_manage.md)

[使用docker-compose创建应用](docs/docker_compose.md)

## 集群管理##

我们使用docker内置的swarm来管理docker集群。

[swarm mode介绍](docs/swarm_mode.md)

我们推荐使用开源的docker集群管理配置方案：

- [Crane](https://github.com/Dataman-Cloud/crane)：由数人云开源的基于swarmkit的容器管理软件，可以作为docker和go语言开发的一个不错入门项目
- [Rancher](https://github.com/rancher/rancher):Rancher是一个企业级的容器管理平台，可以使用Kubernetes、swarm和rancher自研的cattle来管理集群。

[Crane的部署和使用](docs/crane_usage.md)

[Rancher的部署和使用](docs/rancher_usage.md)

## 资源限制

[内存资源限制](docs/memory_resource_limit.md)

[CPU资源限制](docs/cpu_resource_limit.md)

[IO资源限制](docs/io_resource_limit.md)

## 服务发现

下面罗列一些列常见的服务发现工具。

 Etcd:服务发现/全局分布式键值对存储。这是CoreOS的创建者提供的工具，面向容器和宿主机提供服务发现和全局配置存储功能。它在每个宿主机有基于http协议的API和命令行的客户端。[https://github.com/docker/etcd](https://github.com/docker/etcd) 

- [Cousul](https://github.com/hashicorp/consul)：服务发现/全局分布式键值对存储。这个服务发现平台有很多高级的特性，使得它能够脱颖而出，例如：配置健康检查、ACL功能、HAProxy配置等等。
- [Zookeeper](https://github.com/apache/zookeeper)：诞生于Hadoop生态系统里的组件，Apache的开源项目。服务发现/全局分布式键值对存储。这个工具较上面两个都比较老，提供一个更加成熟的平台和一些新特性。
- Crypt：加密etcd条目的项目。Crypt允许组建通过采用公钥加密的方式来保护它们的信息。需要读取数据的组件或被分配密钥，而其他组件则不能读取数据。
- [Confd](https://github.com/kelseyhightower/confd)：观测键值对存储变更和新值的触发器重新配置服务。Confd项目旨在基于服务发现的变化，而动态重新配置任意应用程序。该系统包含了一个工具来检测节点中的变化、一个模版系统能够重新加载受影响的应用。
- [Vulcand](https://github.com/vulcand/vulcand)：vulcand在组件中作为负载均衡使用。它使用etcd作为后端，并基于检测变更来调整它的配置。
- [Marathon](https://github.com/mesosphere/marathon)：虽然marathon主要是调度器，它也实现了一个基本的重新加载HAProxy的功能，当发现变更时，它来协调可用的服务。
- Frontrunner：这个项目嵌入在marathon中对HAproxy的更新提供一个稳定的解决方案。
- [Synapse](https://github.com/airbnb/synapse)：由Airbnb出品的，Ruby语言开发，这个项目引入嵌入式的HAProxy组件，它能够发送流量给各个组件。[http://bruth.github.io/synapse/docs/](http://bruth.github.io/synapse/docs/) 
- [Nerve](https://github.com/airbnb/nerve)：它被用来与synapse结合在一起来为各个组件提供健康检查，如果组件不可用，nerve将更新synapse并将该组件移除出去。

## 插件开发

[插件开发示例-sshfs](docs/plugin_developing.md)

[我的docker插件开发文章](http://rootsongjc.github.io/blogs/docker-plugin-develop/)

[Docker17.03-CE插件开发举例](http://rootsongjc.github.io/blogs/docker-plugin-develop/)

**网络插件**

- [Contiv](http://rootsongjc.github.io/tags/contiv/) 思科出的Docker网络插件，趟坑全记录，目前还无法上生产，1.0正式版还没出，密切关注中。
- [Calico](github.com/calico) 产品化做的不错，已经有人用在生产上了。

**存储插件**

## 业界使用案例

[京东从OpenStack切换到Kubernetes的经验之谈](docs/jd_transform_to_kubernetes.md)

[美团点评容器平台介绍](docs/meituan_docker_platform.md)

[阿里超大规模docker化之路](docs/ali_docker.md)

[TalkingData-容器技术在大数据场景下的应用Yarn on Docker](docs/td_yarn_on_docker.md)

[乐视云基于Kubernetes的PaaS平台建设](docs/letv_docker.md)

## 资源编排

建议使用kuberentes，虽然比较复杂，但是专业的工具做专业的事情，将编排这么重要的生产特性绑定到docker上的风险还是很大的，我已经转投到kubernetes怀抱了，那么你呢？

[我的kubernetes探险之旅](http://rootsongjc.github.io/tags/kubernetes/)

## 相关资源

[容器技术工具与资源](docs/tech_resource.md)

[容器技术2016年总结](docs/container_2016.md)

## 关于

Author: [Jimmy Song](rootsongjc.github.io/about)

rootsongjc@gmail.com

更多关于**Docker**、**MicroServices**、**Big Data**、**DevOps**、**Deep Learning**的内容请关注[Jimmy Song's Blog](http://rootsongjc.github.io)，将不定期更新。