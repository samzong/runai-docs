# Upgrading a Cluster Installation

## Find the current Run:AI cluster version

To find the current version of the Run:AI cluster, run:

```
kubectl get deployment -n runai runai-operator -o yaml \
    -o jsonpath='{.spec.template.spec.containers[*].image}'
```

Run:

```
kubectl apply -f https://raw.githubusercontent.com/run-ai/docs/master/updated_crds.yaml
helm repo update
helm get values runai-cluster -n runai > values.yaml
helm upgrade runai-cluster runai/runai-cluster -n runai -f values.yaml
```

## Verify successful installation

To verify that the upgrade has succeeded run:

```
kubectl get pods -n runai
```

Verify that all pods are running or completed.

