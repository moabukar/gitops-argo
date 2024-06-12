# GitOps layout structure 

## Gitops

The `gitops` repository has 2 main sections

- `/registry`: the argocd gitops application registry for each of our clusters
- `/terraform`: infrastructure as code & configuration as code for your cloud, git provider, vault, and user resources

## Core bootstrap apps

- These core apps have been bootstrapped on the cluster

| Application              | Namespace        | Description                                 | URL (where applicable)             |
| ------------------------ | ---------------- | ------------------------------------------- | ---------------------------------- |
| Argo CD                  | argocd           | GitOps Continuous Delivery                  | https://argocd.test.dev               |
| Argo Workflows           | argo             | Application Continuous Integration          | https://argo.test.dev       |
| Atlantis                 | atlantis         | Terraform Workflow Automation               | https://atlantis.test.dev             |
| Cert Manager             | cert-manager     | Certificate Automation Utility              |                                    |
| Certificate Issuers      | clusterwide      | Let's Encrypt browser-trusted certificates  |                                    |
| Chart Museum             | chartmuseum      | Helm Chart Registry                         | <CHARTMUSEUM_INGRESS_URL>          |
| External Secrets         | external-secrets | Syncs Kubernetes secrets with Vault secrets |                                    |
| Metaphor Development     | development      | Development instance of sample application  | https://metaphor-development.test.dev |
| Metaphor Staging         | staging          | Staging instance of sample application      | https://metaphor-staging.test.dev     |
| Metaphor Production      | production       | Production instance of sample application   | https://metaphor-production.test.dev  |
| Nginx Ingress Controller | ingress-nginx    | Ingress Controller                          |                                    |
| Vault                    | vault            | Secrets Management                          | https://vault.test.dev                |
