# k8s-opa-gatekepper-demo


This project is demoing OPA Gatekeeper with Kubernetes. Gatekeeper is an opensource project supported by CNCF. It aims for creating policies to manage Kubernetes like:
* Enforcing labels on namespaces
* Allowing only images coming from certain Docker Registries
* Require all Pods specify resource requests and limits
* Prevent conflicting Ingress objects from being created.
* Enforcing running containers as non-root.
---

```
# Deploy OPA Gatekeeper
kubectl apply -f https://raw.githubusercontent.com/open-policy-agent/gatekeeper/master/deploy/gatekeeper.yaml

# Scenario: Enforce Having A Specific Label In Any New Namespace
# Deploy the Contraint Template
kubectl apply -f k8srequiredlabels_template.yaml

# Deploy the Constraints
kubectl apply -f all_ns_must_have_gatekeeper.yaml

# Deploy a namespace denied by Policy
kubectl apply -f bad-namespace.yaml

# Deploy a namespace allowed by Policy
kubectl apply -f good-namespace.yaml
```
