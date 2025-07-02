# ELearning_Infrastructure# 📦 ELearning Kubernetes Infrastructure

This repository manages the **Kubernetes infrastructure** for the NovaLearn platform using **GitOps with Argo CD**.

<p align="center">
  <img src="https://skillicons.dev/icons?i=git,kubernetes,docker,gcp" />
  <img src="assets/argocd.svg" height="40" alt="Argo CD" />
</p>
---

## 🧭 Project Structure

```bash
├── argo-cd/
│ └── argocd-app.yaml # Argo CD root Application
├── prod/
│ ├── api/ # API service manifests
│ ├── infra/ # Infrastructure dependencies
│ ├── ingress/ # App routing
│ ├── ml/ # Machine learning services
│ └── transcode/ # Video transcoding service

│ └── namespace.yaml # Namespace definition (nova-learn)
```

---

## 🚀 GitOps via Argo CD

Argo CD watches this repository and automatically syncs resources defined under `prod/` into your Kubernetes cluster.

### 🔧 Argo CD Application (app-of-apps)

> 🌀 This setup enables Argo CD to automatically apply all manifests under the prod/ directory into the nova-learn namespace.

```bash
kubectl apply -f argo-cd/argocd-app.yaml
```

## 🔐 Secrets Management

Secrets are stored as regular \*.secret.yml files in prod/\*\* and applied manually with:

```bash
kubectl apply -f prod/*/*.secret.yml
```

⚠️ These are not encrypted. Make sure not to push \*.secret.yml files to the repository.

## 🧪 Environments

Currently, the repository only includes the prod/ environment.
You can extend this structure like:

```bash
.
├── dev/
├── staging/
├── prod/
```

And manage each via separate Argo CD applications or an ApplicationSet.

---

## 📬 Contributions

This is an internal infrastructure repository. Please use issues and PRs to request changes or propose improvements.
