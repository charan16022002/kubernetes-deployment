# Kubernetes Deployment and Troubleshooting Lab

Deploy a two-replica HTTP demo with readiness/liveness probes and resource requests/limits.

## Deploy

```bash
kubectl apply -f k8s/
kubectl rollout status deployment/sre-demo
kubectl get pods -l app=sre-demo
kubectl get svc sre-demo
kubectl port-forward svc/sre-demo 8080:80
curl http://localhost:8080/
```

## Troubleshooting practice

```bash
kubectl describe deployment sre-demo
kubectl describe pods -l app=sre-demo
kubectl logs -l app=sre-demo --tail=100
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl rollout history deployment/sre-demo
```

The sample uses an inline Python HTTP handler so it can be deployed without pulling a custom image. For a production cluster, use a reviewed, version-pinned application image and your organization's security policies.
