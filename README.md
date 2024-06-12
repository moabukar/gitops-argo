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

## GitOps registry

The argocd configurations in this repo can be found in the [registry directory](./registry). The applications that we build and release on the kubefirst platform will also be registered here in the development, staging, and production folders. The `metaphor` application can be found there to serve as an example to follow for building and shipping code on the platform.

The `main` branch's registry directory represents the gitops desired state for all apps registered with kubernetes. Argo CD will automatically apply your desired state to kubernetes through. You can see the Sync status of all of your apps in [argo cd](https://argocd.test.dev).

## TF - IaC

The terraform in this repository can be found in the [terraform directory](./terraform). It has entry points for management of cloud resources, vault configurations, git provider configurations, and user management.

All of the terraform is automated with a tool called Atlantis that integrates with your git pull requests. To see the terraform entry points and under what circumstance they are triggered, see [atlantis.yaml](./atlantis.yaml).

Any change to a `*.tf` file, even a whitespace change, will trigger its corresponding Atlantis workflow once a pull request is submitted. Within a minute it will post the plan to the pull request with instruction on how to apply the plan if approved.
