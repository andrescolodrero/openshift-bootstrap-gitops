# After Installing ArgoCD

1. Get Rote: oc get routes -n openshift-gitops | grep openshift-gitops-server | awk '{print $2}'
2. getadmin: oc extract secret/openshift-gitops-cluster -n openshift-gitops --to=-
3. For testing add lael to namespace to be controlled by argo:
 oc label namespace <YOUR_NAMESPACE_NAME> \
  argocd.argoproj.io/managed-by=<YOUR_ARGOCD_INSTANCE_NAME>
  
