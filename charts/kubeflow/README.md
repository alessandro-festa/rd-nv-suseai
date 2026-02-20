# Kubeflow Helm Chart

## Usage

[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs/) to get started.

Once Helm is set up properly, add the repo as follows:

```console
helm repo add kubeflow-chart https://mahdikhashan.github.io/kubeflow-helm-chart
helm repo update
```

or to use it as an ArgoCD App

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: kubeflow
  namespace: argocd
  annotations:
    argocd.argoproj.io/compare-options: IgnoreExtraneous
  finalizers:
    - resources-finalizer.argocd.argoproj.io
spec:
  project: default
  source:
    repoURL: https://github.com/mahdikhashan/kubeflow-helm-chart
    targetRevision: main
    path: chart
  destination:
    server: https://kubernetes.default.svc
    namespace: kubeflow
```

---

[LICENCE](https://github.com/mahdikhashan/kubeflow-helm-chart/blob/main/LICENCE)
