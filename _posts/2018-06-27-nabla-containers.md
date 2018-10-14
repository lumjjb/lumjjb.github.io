---
layout: post
title: "Nabla containers: a new approach to container isolation"
---

One of the projects I am working on at IBM Research is Nabla Containers. It is a resaerch effort on how to address container security isolation problems!

[Check it out on here!](https://nabla-containers.github.io/)


## Preview

Despite all of the advantages that have resulted in an industry-wide shift towards containers, containers have not been accepted as isolated sandboxes, which is crucial for container-native clouds. We introduce nabla containers, a new type of container designed for strong isolation on a host.

Nabla containers achieve isolation by adopting a strategy of attack surface reduction to the host. A visualization of this approach appears in this figure:

![NablaContainers]({{ '/public/img/posts/2018-06-27-nabla-containers/nabla-containers.png' | relative_url }})
