NGINX KUBERNETES LAB
30 individual YAML manifests + command reference.
Start with namespace, deployment and ClusterIP service. Commands file gives order.
Do not apply the entire directory blindly. Each workload is a separate exercise.
Minikube: standard StorageClass is assumed for StatefulSet; inspect kubectl get sc.
StatefulSet is a storage/identity demonstration, not Nginx replication.
PV/PVC pair uses hostPath, for single-node lab only; not mounted automatically by other workloads.
Advanced deployment mounts ConfigMap as document root.
Ingress needs a compatible nginx controller and reachable address. NetworkPolicy needs supporting CNI.
LoadBalancer needs implementation (minikube tunnel in lab).
HPA requires Metrics Server. VPA requires separate installation; Off mode avoids modifying CPU/memory requests while HPA uses those metrics.
When using HPA continuously, migrate away from managing Deployment replicas declaratively to avoid reset on apply.
Argo CD examples need installed CRDs/controllers, actual Git URL and valid nginx-base path. Put namespace and intended workload/service in Git, not all exercises. Choose Application OR ApplicationSet for same resources to avoid ownership conflicts.
Secret contains dummy cleartext, not production credentials. Job/CronJob run nginx -t, not long-running web servers.
YAML syntax parsed locally; live Kubernetes API validation not performed. Use server dry-run individually after prerequisites are installed.
Command reference is extensive but not every possible kubectl command. Use kubectl --help and kubectl explain for additional options.

Existing nginx namespace mein workloads ho sakte hain: pehle kubectl get all,pvc -n nginx check karo. Namespace delete karne se purane workloads bhi delete honge. Existing Deployment ka immutable selector different ho toh separate lab cluster use karo. NodePort 30081 available hona chahiye. StatefulSet cache mount sirf storage demo hai; website default document root se serve hogi.
