```yaml
apiVersion: app.redislabs.com/v1alpha1
kind: RedisEnterpriseRemoteCluster
metadata:
  name: new-york-1
  labels:
    app: redis-enterprise
spec:
  # The name of the REC that the RERC is pointing at.
  recName: rec

  # The namespace of the REC that the RERC is pointing at.
  recNamespace: ns1

  # The URL of the cluster, will be used for the active-active database URL.
  apiFqdnUrl: testapi-new-york-1-ns1.redislabs.com

  # The database URL suffix, will be used for the active-active
  # database replication endpoint and replication endpoint SNI.
  dbFqdnSuffix: -example-new-york-1-ns1.redislabs.com

  # The name of the secret containing cluster credentials.
  # Needs to be formatted as: "redis-enterprise-<RERC name>"
  secretName: redis-enterprise-new-york-1
```
