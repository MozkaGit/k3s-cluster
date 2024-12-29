# K3s Cluster GitOps

This repository contains the GitOps configuration of my personal K3s cluster, managed with FluxCD. The infrastructure is deployed on a K3s cluster and uses a GitOps approach for application and infrastructure management.

## Project Structure

```
.
├── apps/                  # Applications deployed on the cluster
├── infrastructure/        # Infrastructure components (controllers)
├── monitoring/           # Monitoring stack (Grafana)
└── clusters/            # Cluster-specific configuration
```

## Deployed application

- **Linkding**: Self-hosted bookmark manager 
- **Audiobookshelf**: Audio book and podcast server
- **Grafana**: Visualization and monitoring

## Infrastructure

### Main components

- **External DNS**: Automatic DNS record management with Cloudflare
- **Cloudflare Tunnel**: Secure tunnel for service access
- **Renovate**: Automatic dependency updates

## Security

- Using SOPS to encrypt secrets
- Secret management with Age
- Secure integration with Cloudflare for service exposure

## Prerequisites

- K3s cluster up and running
- Flux CD installed
- Cloudflare account with configured domain
- Age key for decrypting secrets

## Deployment

1. Clone repository
2. Configure SOPS/Age secrets
3. Apply Flux configuration:

```bash
flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=k3s-cluster \
  --branch=main \
  --path=./clusters/staging
  --personal
```

## Monitoring

The monitoring stack include:
- Prometheus
- Grafana
- Alertmanager

## Maintenance

The project uses Renovate for automatic maintenance of image versions and Helm charts.
