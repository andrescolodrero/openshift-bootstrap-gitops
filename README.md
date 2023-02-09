# Introduction 
OpenShift Platform Administrator repository

This is typically focused on getting the Openshift cluster bootstrapped and configured with the necesarry components to run applications.

Starts as 1 repo:1 cluster, but can be modified for multiple clusters.

Folder structure

## Folder structure:

- cluster-config 
        bootstrap
        - argo-applications
        - argo-projects
        - base
        - overlays
        components
        - argocd-config
        - sealed-secrets
        - argocd-projects
        - argocd-applications
platform-services
- in case we need to add some services as service mesh, operators, etc
data-services
- in case we need to add data services like redis, sql, etc in bootstrap

NOTE: Applications are refernced to other project (now on AzureDevops.. to change to github)

## Sealed Secrets
This repo uses sealed secrets.

Sealed Secrets repo: https://github.com/bitnami-labs/sealed-secrets

Sealed secrets can be used:
There are a number of use-cases where this is a really great concept.

1. GitOps - Storing your YAML manifests in Git and using GitOps tools to sync the manifests to your clusters (For example Flux and ArgoCD!)

2. Giving a team access to secrets without revealing the secret material.

# Requisites:
Install Secret Sealed Controller (Boostrap)
Install kubeseal: https://github.com/bitnami-labs/sealed-secrets/releases

Secret Sealed is installed in the namespace "sealed-secrets". 

To seal credentials:
kubeseal -f creds.yaml --controller-name sealed-secrets --controller-namespace sealed-secrets -o yaml > test.yaml
kubectl apply -f test.yaml


# HOW TO APPLY
1. Build basic bootstrap (if helm chart are in the recipes)
kustomize build --enable-helm bootstrap/overlays/sandbox/ 

2. Apply 
kustomize build --enable-helm bootstrap/overlays/sandbox/ | kubectl apply -f -

3. If there is no Helm Chart
kubetcl -k /bootstrap/overlays/sandbox



cluster-config -> Kustomize managged
    bootstrap
    - base
    - overlays
    components
    applications
     (set argo cd apps)
applications
platform-services
data-services
(argo cd managed)
