# Dapr with FHIR 🔥

An experiment in building cloud native microservices, using [Dapr](dapr.io) and the [FHIR](https://hl7.org/fhir/) data exchange standard in a containerized environment.

## Goals

- Learn by experimenting with RabbitMQ, Redis, and Elastic for an upcoming job
- Build a proof of concept system using a microservice architecture
- Learn and implement the [virtual actor pattern](https://docs.microsoft.com/en-us/dotnet/architecture/dapr-for-net-developers/actors) to see if it's a good fit for this experiment
- Delve more deeply into Dapr, Docker, Kubernetes, and Rancher

## Overview

Implement a simplified version of a patient workflow system in a healthcare setting.

TODO: Add diagrams showing [architecture](https://docs.microsoft.com/en-us/dotnet/architecture/dapr-for-net-developers/media/the-world-is-distributed/distributed-design.png) and workflow [sequence](https://docs.microsoft.com/en-us/dotnet/architecture/dapr-for-net-developers/media/sample-application/sequence.png).

### Microservices

- `AdtService` - Simulated patient administration system for admitting patients to hospital
- `LabService` - Simulated laboratory system for analyzing pathology results
- `AlertService` - Service for generating events based upon specific adverse pathology results

### Applications

- A website showing current inpatients with real-time alerting as laboratory results are available
- Benchmarking to test the performance of the microservices as they work and interact with each other

## Tech stack
- Microservices are written in C# 10 / .NET 6
- [Dapr](https://docs.dapr.io/concepts/overview/) as the distributed application runtime providing cloud abstraction and observability
- [gRPC](https://docs.dapr.io/operations/configuration/grpc/) for communication between services and applications
- [Redis](https://docs.dapr.io/reference/components-reference/supported-state-stores/setup-redis/) as the state stores for patient and lab data
- [RabbitMQ](https://docs.dapr.io/reference/components-reference/supported-pubsub/setup-rabbitmq/) as the pubsub broker for patient admissions and alerting
- [Elastic](https://docs.dapr.io/operations/monitoring/logging/fluentd/) for searching all event logs generated in the system and collected by [Fluentd](https://www.fluentd.org/)
- [Docker](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-with-docker/) containers running on Linux servers orchestrated by [Kubernetes](https://docs.dapr.io/operations/hosting/kubernetes/kubernetes-overview/) and managed via [Rancher](https://rancher.com/why-rancher)

## Building

### Installing

Assumes Windows 10+ with WSL 2 enabled. See installation guides for git|dapr|docker|k8s if not already installed.

```shell
> git --version
git version 2.30.0.windows.2

> git clone https://github.com/si618/dapr-with-fhir.git
Cloning into 'dapr-with-fhir'...

> cd .\dapr-with-fhir\src

> dapr --version
CLI version: 1.6.0
Runtime version: 1.6.0

> docker --version
Docker version 19.03.12, build 0ed913b8-

> docker run -d --restart=unless-stopped -p 80:80 -p 443:443 --privileged rancher/rancher
Unable to find image 'rancher/rancher:latest' locally
latest: Pulling from rancher/rancher...

> kubectl version
Client Version: ...
Server Version: ...

```

### Compiling

TODO: Describe how to compile each service and application (create powershell script to build all?)


## Running

TODO: Describe how to start each service as well as run the benchmark performance tests
