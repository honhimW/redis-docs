```yaml
kind: ClusterRoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: redis-enterprise-operator
  labels:
    app: redis-enterprise
subjects:
- kind: ServiceAccount
  namespace: NAMESPACE_OF_SERVICE_ACCOUNT
  name: redis-enterprise-operator
roleRef:
  kind: ClusterRole
  name: redis-enterprise-operator
  apiGroup: rbac.authorization.k8s.io
```
