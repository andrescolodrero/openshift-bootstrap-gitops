1. Install gitops-operator
2. Configure ArgoCD Repos
3. Seal Credentials:
kubeseal -f argocd-isitopenshiftdemo-creds.yaml --controller-name sealed-secrets --controller-namespace sealed-secrets -o yaml > argocd-isitopenshiftdemo-creds-sealed.yaml

kubeseal -f argocd-isitopenshiftcluster-creds.yaml --controller-name sealed-secrets --controller-namespace sealed-secrets -o yaml > argocd-isitopenshiftcluster-creds-sealed.yaml