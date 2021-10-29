# Gazelle-cni

#### Motivation

As a user-mode protocol stack that has been commercialized within Huawei, Gazelle supports TCP/UDP protocol stack. Compared with similar software, Gazelle has many advantages in performance and applicability, including concurrent linearity, low latency, ease of use, etc. 

The effect of reference performance acceleration Nginx is as follows:

![img](https://gitee.com/openeuler/gazelle-cni/raw/master/Nginx-2.png)

Linearity is close to 1

![img](https://gitee.com/openeuler/gazelle-cni/raw/master/nginx-1.png)

Delays in transmission are shorter.

Ease of use: Without code modification or application recompilation, it can be used immediately after it is installed using the acceleration library.

The Gazelle-CNI project aims to make Huawei's commercial Gazelle project open-source and apply it to cloud-native scenarios to accelerate Service Mesh.

In the various cloud-native scenarios, Service Mesh has become a standard component to implement Istio. As the data plane component of Istio, Envoy matters a lot. Therefore, the goal of this project is to accelerate Envoy. 
#### Objectives

Performance: Improve the performance of the service mesh data plane, reduce the service access latency in a cluster by 30%, and increase the service access throughput in a cluster by 30%.

Ease of use: Without code modification and recompilation, the open-source Istio can be used immediately after it is deployed.

#### Overview

As the data plane component of Istio, Envoy manages all external data flows in the mesh and implements LB, statistics and other functions.  The data flow figure is as follows:

![img](https://gitee.com/openeuler/gazelle-cni/raw/master/envoy-1.png)

From the preceding figure, we can see that the entire data flow path is long, bringing bottlenecks to the performance of the service mesh. =Therefore, the entire process needs to be accelerated. The acceleration solution is as follows:

![img](https://gitee.com/openeuler/gazelle-cni/raw/master/envoy-2.png)

The acceleration parts include:

1.	Gazelle CNI: Optimized based on Gazelle.
2.	Socket-map: eBPF sockmap technology is used to accelerate the communication between sockets.
3.	XDP Bridge: XDP technology is used to implement the bridge function. XDP Bridge serves as the default bridge of Kubelet.

#### Roadmap Planning (Tentative)

1.	Open-source Gazelle project: make the source code open-source by June 30th, 2021.
2.	Gazelle-CNI technology demonstration: The demonstration will be done by March 30th, 2021. Envoy can simultaneously apply to the Gazelle protocol stack and the kernel protocol stack to complete single-node acceleration.
3.	Gazelle-CNI technology development: Complete the CNI adaptation to the Gazelle project and AF_XDP adaptation by May 30th, 2021b.
4.	Socket-map technology: Technology development will be completed before by June 30th, 2021.
5.	XDP bridge technology: Technology development will be completed by July 30th, 2021.

#### Join Us

Though Gazelle technology is mature, we still need help with the design and verification of Gazelle-CNI and other technologies. Please join us, if you are interested in our project.
#### Contact Us

[high-performance-network@openeuler.org](mailto:high-performance-network@openeuler.org) [dev@openeuler.org](mailto:dev@openeuler.org)