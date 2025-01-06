## Evaluating Docker with CIS Benchmark and Docker-bench

### Build Image

```
docker build . -t opensuse/leap:latest -m 256mb --no-cache=true
```

### Install Docker-bench

Clone the Docker-bench repository from GitHub:
```
git clone https://github.com/aquasecurity/docker-bench.git
cd  /docker-bench 
go build -o docker-bench
```

### Analyze Docker

```
./docker-bench --include-test-output > docker-bench.txt 
```
Concatenate the docker-bench.txt file and look for the lines where there is a failure:
```
cat docker-bench.txt | grep FAIL
```
This command returns the checks that failed. In the next demo, we will look at these checks more closely, pick one of the failed checks, harden that check, then rerun Docker-bench to show that the failed check has been fixed.


export POD_NAME=$(kubectl get pods --namespace falco -l "app.kubernetes.io/name=falco-exporter,app.kubernetes.io/instance=falco-exporter" -o jsonpath="{.items[0].metadata.name}")
echo $POD_NAME
kubectl port-forward --namespace falco $POD_NAME 9376

export KUBECONFIG="/etc/rancher/rke2/rke2.yaml"
export PATH=$PATH:/var/lib/rancher/rke2/bin
alias k=kubectl

helm upgrade prometheus prometheus-community/kube-prometheus-stack \
  --set prometheus.prometheusSpec.scrapeInterval="15s" \
  --set prometheus.prometheusSpec.evaluationInterval="15s" \
  --namespace monitoring

helm repo update

helm install prometheus prometheus-community/kube-prometheus-stack \
  --set prometheus.prometheusSpec.scrapeInterval="15s" \
  --set prometheus.prometheusSpec.evaluationInterval="15s" \
  --namespace monitoring

helm install prometheus prometheus-community/kube-prometheus-stack \
  --set prometheus.prometheusSpec.scrapeInterval="15s" \
  --set prometheus.prometheusSpec.evaluationInterval="15s" \
  -f values.yaml \
  --namespace monitoring

helm install prometheus prometheus-community/kube-prometheus-stack -f values.yaml --namespace monitoring

helm show values prometheus-community/kube-prometheus-stack --namespace monitoring > prometheus-default-values.yaml
helm uninstall prometheus --namespace monitoring
helm upgrade prometheus prometheus-community/kube-prometheus-stack --namespace monitoring -f new-values.yaml --dry-run

kubectl exec --stdin -it falco-vswsv  --namespace falco -- /bin/bash

adduser best_hacker
cat /etc/shadow > /dev/null
cat /etc/passwd > /dev/null_2

kubectl port-forward -n monitoring svc/prometheus-kube-prometheus-prometheus  --address 0.0.0.0  9090:9090
kubectl --namespace monitoring port-forward svc/prometheus-grafana --address 0.0.0.0 3000:80

k exec -it -n monitoring prometheus-prometheus-kube-prometheus-prometheus-0 -- /bin/sh