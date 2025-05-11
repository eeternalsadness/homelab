# Homelab

## Introduction

This is my personal homelab where I experiment with container orchestration and infrastructure management. I try to run different kinds of technology here to have a better understanding of them. I'll try to follow DevSecOps best practices where I can.

## Setup

Currently I'm running a 2-node cluster on my spare hardware. I'm using `k3s` on Ubuntu Server.

**Control plane**:

Surface Go (1st gen): Pentium 4415Y (2 cores, 4 threads), 4GB RAM

**Worker nodes**:

ASRock Deskmini A300: AMD Ryzen 3 2200G (4 cores, 4 threads), 8GB RAM

## Workload

### Infrastructure

- ArgoCD
- Cert Manager
- Prometheus
- Grafana
- HashiCorp Vault
- Qdrant

I'm currently using Terraform to manage these infrastructure components:

- Grafana: [https://github.com/eeternalsadness/grafana](https://github.com/eeternalsadness/grafana)
- Vault: [https://github.com/eeternalsadness/vault](https://github.com/eeternalsadness/vault)

## Decisions

### VPN

I used to run an OpenVPN service on the Deskmini node with Fail2ban as a tiny safeguard to allow remote access to my cluster, but my home network was very bad, so managing the cluster remotely was really frustrating. I ended up removing the OpenVPN service and decided to work on a local minikube cluster when I'm away from home instead.

I'll probably revisit this in the future with Cloudflare tunnel.

### ArgoCD

I'm starting out with ArgoCD as my GitOps tool of choice based on my past experience. I'm currently implementing the app of apps pattern for cluster management.

I'll try out FluxCD in the future and make a decision on which tool I like better.
