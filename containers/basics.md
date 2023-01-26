---
title: 'Basics'
metaTitle: 'Containers | DevNotes'
metaDescription: 'Containers | DevNotes'
sidebar_category_label: Containers
---

# Containers

- Containers offer the same abilities as a Virtual Machine but with less overhead.
- Containers do not virtualize a complete OS

## Used for

- Software Portability -- Running software consistentyl on different machines
- Isolation -- Keeping individual pieces of software separate from one another
- Scaling -- Increasing or decreasing resource sallocated to software as needed
- Automation -- Automating processes to save time and money
- Efficient Resources Usage -- Containers use resources efficiently, which saves money

## Advantages

- Isolation and portability of VMs
- More lightweight thean VMs - Less resources usage
- Faster than VMs -- Container can start in seconds
- Smaller than VMs -- Container images canb e measured in megabutes, not gigabytes

## Limitations

- Less flexible than VMs -- You can't run a Windows container on a Linux machine.
- Introduces new challenges around orchestration and automation

## [Docker](https://www.docker.com/)

- A container runtime, which actually allows you to implement container. (Container is just a concept)
- Allows you to build and manage containers and container images

## Other Container Runtimes

- [rkt ](https://coreos.com/rkt/)
  - Ultimately does the same thing as Docker.
  - Is more linux like and may be easier for linux stuff
  - Supports more container images formats than Docker
- [containerd ](https://containerd.io/)
  - Emphasizes simplicity, robustness, portability
  - Focused solely on running containers
  - Does not has many features as Docker but may not be a downside
