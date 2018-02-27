# Istio on Kubernetes

To install Istio on Kubernetes it's recommended to use Kubernetes >= 1.9.0 and use the auto-injection functionality. To run this on minikube you have to use minikube >= 0.25 and select version >=1.9.0 of Kubernetes. You also have to enable different other features. Ref. https://istio.io/docs/setup/kubernetes/sidecar-injection.html#automatic-sidecar-injection

```bash
minikube start \
        --extra-config=controller-manager.ClusterSigningCertFile="/var/lib/localkube/certs/ca.crt" \
        --extra-config=controller-manager.ClusterSigningKeyFile="/var/lib/localkube/certs/ca.key" \
        --extra-config=apiserver.Admission.PluginNames=NamespaceLifecycle,LimitRanger,ServiceAccount,PersistentVolumeLabel,DefaultStorageClass,DefaultTolerationSeconds,MutatingAdmissionWebhook,ValidatingAdmissionWebhook,ResourceQuota \
        --kubernetes-version=v1.9.0
```

```bash
curl -L https://git.io/getLatestIstio | sh -
cd istio-0.5.1
kubectl apply -f install/kubernetes/istio-auth.yaml
```

Manually download missing scripts (only required for istio < 0.5.1)

```bash
cd install/kubernetes
wget https://raw.githubusercontent.com/istio/istio/master/install/kubernetes/webhook-create-signed-cert.sh
wget https://raw.githubusercontent.com/istio/istio/master/install/kubernetes/webhook-patch-ca-bundle.sh
chmod +x webhook-*
cd ../..
```

Install ca bundle.

```bash
kubectl apply -f install/kubernetes/istio-sidecar-injector-configmap-release.yaml
cat install/kubernetes/istio-sidecar-injector.yaml | \
     ./install/kubernetes/webhook-patch-ca-bundle.sh > \
     install/kubernetes/istio-sidecar-injector-with-ca-bundle.yaml
kubectl apply -f install/kubernetes/istio-sidecar-injector-with-ca-bundle.yaml
```

Verify that the installation of the sidecar injector was successfully.

```bash
kubectl -n istio-system get deployment -listio=sidecar-injector
```
## Bookinfo tutorial

This tutorial shows some of the main features in Istio.

Link: [Bookinfo](https://istio.io/docs/guides/bookinfo.html) We haven't tested it on minikube by our self.
