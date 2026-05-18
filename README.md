# Homelab

## Introduction

This is my personal homelab where I experiment with container orchestration and infrastructure management.

## Setup

Kubernetes cluster on Talos Linux. The Talos nodes are provisioned as VMs through Proxmox on my spare hardware.

**Proxmox hosts**:

- ASRock Deskmini A300: AMD Ryzen 3 2200G (4 cores, 4 threads), 8GB RAM
- AMD Ryzen mini PC: 8 cores, 16 threads, 32GB RAM

## Related Repos

- [homelab-ansible](https://github.com/eeternalsadness/homelab-ansible) — Pi-hole DNS server and other node-level config
- [cloudflare](https://github.com/eeternalsadness/cloudflare) — Cloudflare Tunnel and DNS managed through Terraform
- [grafana](https://github.com/eeternalsadness/grafana) — Grafana config managed through Terraform
- [vault](https://github.com/eeternalsadness/vault) — Vault config managed through Terraform

## Workload

### Cluster Infrastructure

- ArgoCD (app of apps pattern)
- Traefik (ingress controller)
- cert-manager
- MetalLB
- external-dns
- external-secrets
- kube-prometheus-stack (Prometheus + Grafana)
- HashiCorp Vault

### AI Infrastructure

- MCP servers (Kubernetes MCP server)

### Applications

- Homepage (internal dashboard)

## Decisions

### Remote Access

I used to run an OpenVPN service with Fail2ban for remote cluster access, but it was unreliable on my home network. I've since moved to Cloudflare Tunnel, with the configuration managed in the cloudflare repo.

### GitOps

ArgoCD with the app of apps pattern for cluster management.
