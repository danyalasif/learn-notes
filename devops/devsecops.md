---
title: "DevSecOps"
metaTitle: "DevSecOps | DevNotes"
metaDescription: "DevSecOps | DevNotes"
---

# [DevSecOps Essentials](https://linuxacademy.com/cp/modules/view/id/266)

* DevSecOps is new
* Published first report in May 2016 by Gartner

## About this course
DevOps and DevSecOps are about culture, "the attitudes and behaviour of a particular social group"

* DevSecOps builds on the idea that cross-functional teams must work together and that everyone is responsible for security
* DSO is also about automation
* DevSecOps inherits directly from DevOps with an added security group
* DevSecOps is a mashup of Development, Security, and Operations

## 1.1 - Overview of DevSecOps

### Agile Development
* Teams have started utilizing extreme programming and scrum methodology to improve productivity
* By breaking up large releases, that could take months, into small batches of feature changes that only take days or weeks, teams can drastically shorten time to market
* Kaizen (Continuous Improvement)
* Agile teams become more productive, Potentially Shippable Increment build up in staging and Quality Assurance
* Even though agile teams build things faster, these changes are not pushed because of bottlenecks in deployment


### Security Monitoring
* After applications and systems have been promoted to production they are continuously monitored for vulenrabilities
* Depending on the severity of an identified vulnerability, application might be removed from production or simply cleansed of the vulnerability
* Typically, **remediation** involves the development organization, **as refactoring** may be required in order to update ocmponent libraries to version that have eliminated the threat

## 1.2 Cyber Security Standards and Concepts

### Attack Surface
* The **attack surface** of a system is the collection of points (**attack vectors**) where an unauthorized user (**attacker**) may enter to inject data to or extract data from an environment
* Keeping the attack surface as small as possible is a basic security goal

### Malware and Vulnerabilites
* Malware is malicious software that attackers deploy to infect individual computers or entire digitial network
* Malware exploits target system vulnerabilites that can be hijacked, such as bugs in legitimate software
* Vulnerability is a weakness or deficiency in a computer system that an attacker can exploit to perform unauthorized actions within the system

### The OpenSCAP Project
* Security Content Automation Protocol (SCAP) is a US security standard maintained by NIST
* A set of open source tools for implmenting and enforce standards







# Draft:
### Software Onboarding
* Firewall systems prevent outside attackers from accessing internal systems
* At the time of onboarding software should be scanned for known vulnerabilites
* On-premise systems must be hardened


### Docker Bench

A software tool that analyzes server infrastrucutres and docker components -- Can be run regularly to find out any vulnerabilities in Docker

Helps in Host Hardening
Helps with common mistakes of creating users within the Docker group. This is known vulnerability allows privlidge escalation on a spawned container process
Audit the file system againast the Docker directories to receive early warnings
Containers allow network bridging to be limited only those ports necessary for particular application within container instance
ulimit ca be set to ensure that the container to limite to a specifized maximum number of open file descriptor
Container should be prohibited from acuqiring new privilidges
TUF
Container image signing and verification policies