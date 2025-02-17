# Flux GitOps Configuration

This directory contains the Flux GitOps configuration for multiple Kubernetes clusters.

## Repository Structure

```
flux/
├── clusters/
    ├── staging/
    │   ├── namespace.yaml        # Staging namespace definition
    │   ├── deployment.yaml       # Sample application deployment
    │   └── kustomization.yaml    # Kustomization for staging resources
    └── development/
        ├── namespace.yaml        # Development namespace definition
        ├── deployment.yaml       # Sample application deployment
        └── kustomization.yaml    # Kustomization for development resources
```

## Bootstrap Instructions

To bootstrap a new cluster with Flux, use the following command:

```bash
flux bootstrap github \
  --owner=<github-username> \
  --repository=<repo-name> \
  --branch=main \
  --path=./clusters/<cluster-name> \
  --personal
```

Replace the placeholders:
- `<github-username>`: Your GitHub username
- `<repo-name>`: The name of your GitOps repository
- `<cluster-name>`: The name of the cluster (e.g., 'staging' or 'development')

## Configuration Details

### Staging Environment
- Namespace: staging-apps
- Sample deployment with 2 replicas
- Higher resource limits for production-like testing

### Development Environment
- Namespace: development-apps
- Sample deployment with 1 replica
- Lower resource limits for development purposes