```yaml
apiVersion: app.redislabs.com/v1alpha1
kind: RedisEnterpriseActiveActiveDatabase
metadata:
  name: reaadb
  labels:
    app: redis-enterprise
spec:
  participatingClusters:
    # Participating cluster pointing to RERC named: 'new-york-1'.
    - name: new-york-1

    # Participating cluster pointing to RERC named: 'boston-1'.
    - name: boston-1
```
