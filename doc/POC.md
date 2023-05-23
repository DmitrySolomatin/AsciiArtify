## AsciiArtify Proof of Concept (PoC) - ArgoCD Deployment

##Overview

This document provides step-by-step instructions for deploying ArgoCD on a Kubernetes cluster as part of the AsciiArtify Proof of Concept (PoC). ArgoCD is a GitOps continuous delivery tool that enables declarative configuration and management of applications in Kubernetes.

Please follow the steps below to install and configure ArgoCD for the AsciiArtify PoC.

## Prerequisites

Before proceeding with the installation, ensure that you have the following prerequisites:

A running Kubernetes cluster
kubectl command-line tool configured to access the cluster
Helm package manager
Steps:

Install ArgoCD using Helm:

$ helm repo add argo https://argoproj.github.io/argo-helm
$ helm install argocd argo/argo-cd --namespace argocd

Verify the installation:

$ kubectl get pods -n argocd

Ensure that all ArgoCD pods are in the "Running" state before proceeding.

Expose the ArgoCD API server:

$ kubectl port-forward svc/argocd-server -n argocd 8080:443
Access the ArgoCD Web UI:
Open a web browser and navigate to https://localhost:8080 (replace "localhost" with the appropriate IP or hostname if accessing from a remote machine).
Accept any security warnings or self-signed certificate prompts.
Login using the default username and password:
Username: admin
Password: $(kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d)
Once logged in, you will have access to the ArgoCD interface, where you can manage applications, repositories, and perform GitOps operations.


## Conclusion

By following these steps, you have successfully deployed and accessed the ArgoCD interface for the AsciiArtify PoC. You can now proceed with further configuration and deployment of applications using the ArgoCD GitOps workflow.

For more information and advanced usage of ArgoCD, refer to the official documentation: ArgoCD Official Documentation

Please note that this demo example is based on the official ArgoCD documentation and may require adjustments based on your specific environment and requirements.

Note: Ensure to update the instructions with the appropriate IP or hostname when accessing the ArgoCD Web UI from a remote machine.

This document is part of the AsciiArtify PoC documentation and should be referenced for the deployment and access of ArgoCD.
