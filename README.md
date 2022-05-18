## Redis with redistimeseries on Kubernetes & Grafana

### Install Redis

https://www.containiq.com/post/deploy-redis-cluster-on-kubernetes

### Install the grafana redis data source

1. `kubectl exec -it <grafana-service-name> -- sh`
1. `grafana-cli plugins install redis-datasource` (reference: https://redis.com/blog/introducing-the-redis-data-source-plug-in-for-grafana)
1. restart the grafana pod: `kubectl rollout restart deployment grafana`
1. restart the tunnel forwarding: `kubectl port-forward service/grafana 3000:3000`
1. go to the data sources, and now add the redis one
1. use the endpoint of one of the internal redis nodes, with the port, i.e: `redis-0.redis.redis.svc.cluster.local:6379` and for password: `a-very-complex-password-here`
1. now Grafana should be connected with Redis!
