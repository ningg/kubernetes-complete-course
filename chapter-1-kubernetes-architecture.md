<!-- $theme: default -->
<!-- $size: 16:9 -->
<!-- footer: @jolestar -->


# Kubernetes 完全教程
## Kubernetes 架构概述

### 王渊命 @jolestar

![bg](images/bg.png) 

---
# Agenda

1. Kubernetes 为何而生 
1. Kubernetes 的架构
 

---
# Kubernetes 为何而生 - 云发展到一个新阶段

## IaaS 云解决了哪些问题

IaaS 云，解决了下述问题：

* `按需`购买
* 接管`硬件`资源的`运维`
* 提供`可编程接口`来管理资源
* 提供 SDN、SDS， 模拟硬件`网络`以及`存储`

补充：

* **SDN**：Software Defined Network，**软件定义网络**
	* `硬件`网络，由`软件`集中式管理
	* `可编程化`，控制`转发层面`区分开
	* 不是具体的一项技术，不是具体的协议，而是一个思想、一个框架
* **SDS**：Software Defined Storage，**软件定义存储**
	* 硬件中的存储控制器功能，放到软件层面
	* 包括：卷管理、RAID、数据保护、快照和复制等
	* 如果存储控制器功能被抽离出来，该功能就可以放在基础架构的任何一部分，例如
		* 特定的硬件上
		* hypervisor内部
		* 虚机内部

## 特点

特点：

* **解耦**：对`应用`无侵入
* **面向资源**：直接分配硬件资源即可

> 用户，从关注`资源的运维`，转向关注`应用的开发`和`应用的运维`成本.


---
# Kubernetes 为何而生 - 容器的成熟奠定了基础

## 容器（Docker/Moby） 解决了哪些问题


1. **安装文件**：应用`安装包`的标准化（`Image`）
1. **运行环境**：应用`进程`的标准化（`Container`）


## 特点

特点：

> `单进程`的**标准化**


---
# 容器编排系统应运而生

我们需要一种 **面向应用（Application Oriented）** 的系统，来降低服务端应用的`开发`和`部署运维`成本

> We wanted people to be able to **program** for the data center just like they program for their laptop --Ben Hindman

我们再引申一下，从开发延伸到**部署运维**

> We wanted people to be able to manager app for the data center just like they manager app on their laptop

---
# Borg, Mesos, Omega, and Kubernetes

1.《[Borg, Omega, and Kubernetes](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/44843.pdf)》

2.Mesos vs Kubernetes


---
# Mesos 

![mesos](images/mesos-arch.jpg)

更多细节：

* [Mesos 架构以及源码浅析](http://jolestar.com/mesos-architecture/)


---
# Mesos vs Kubernetes

1. 编程框架 vs. 运行平台
2. 资源共享 vs. 定义状态
3. 分布式调度 vs. 状态控制器

> define a minimal interface that enables efficient resource sharing across frameworks, and otherwise push control of task scheduling and execution to the frameworks -- mesos

> Kubernetes is not a mere “orchestration system”; it eliminates the need for orchestration. The technical definition of “orchestration” is execution of a defined workflow: do A, then B, then C. In contrast, Kubernetes is comprised of a set of independent, composable control processes that continuously drive current state towards the provided desired state. It shouldn’t matter how you get from A to C: make it so. -- kubernetes


---
# Kubernetes 的架构 - 始于编排而超越编排

Kubernetes 架构：

1. **部署**架构
2. **逻辑**架构


---

<img src="images/k8s-arch1.png" height="700"/>

---
# Kubernetes 逻辑架构

1. Declare，Observe，React
1. 一个状态存储
1. 多个控制器


---

<img src="images/k8s-arch2.png" height="700"/>

---
# Kubernetes 的架构优势

1. 自愈 （最终一致）
1. 组合 （低级组件组合成高级组件）
1. 面向未来 （API 定义目标，而不是过程）

```yaml
apiVersion: vx
kind: API-Sla
metadata:
  name: myservice-sla
spec:
  percent: 99%
  latency: 200ms
  cost: x$/h
  selector:
    app: myapp
  
```


---
# Kubernetes 的架构劣势

1. 同步操作需求比较难实现
2. 非状态操作不好实现 

---
# Kubernetes 尚未解决的问题（开放式问题）

1. 配置管理 ([Declarative application management in Kubernetes](https://docs.google.com/document/d/1cLPGweVEYrVqQvBLJg6sxV-TrE5Rm2MNOBA_cxZP2WU))
2. 服务依赖

---
# 作业

1. 阅读本次课程中给出的论文，以及 Kubernetes 的官方文档，结合自己的编程运维经验，思考 Kubernetes 能解决你遇到的哪些问题，哪些可能解决不了。
2. 手动搭建一个 Kubernetes 进行试验，初步熟悉 Kubernetes 的命令以及 API。（推荐通过 QingCloud青云的 appcenter 进行部署。https://appcenter.qingcloud.com/apps/app-u0llx5j8）


---
### 关于我

个人博客: [http://jolestar.com](http://jolestar.com)

![about](http://jolestar.com/images/weichat/qrcode_jolestar_blog2.png)

---

<img style="width:100%;height=100%;margin:0;padding:0;" src="images/about-us.png"/>

