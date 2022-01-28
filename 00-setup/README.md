# Demo Setup

## 1. Advanced Cluster Management for Kubernetes (ACM)

The demos are deployed and configured using ACM.  To deploy ACM (ideally to a "hub" cluster, but this will also work if deployed to the "demo" cluster):

1. Deploy the ACM Operator
```
oc apply -k https://github.com/redhat-cop/gitops-catalog/advanced-cluster-management/operator/overlays/release-2.4
```
2. Once the Operator finishes deploying, deploy an instance of ACM:
```
oc apply -k https://github.com/redhat-cop/gitops-catalog/advanced-cluster-management/instance/base
```

## 2. Advanced Cluster Security for Kubernets (ACS)

Once ACM finishes deploying, you can create the following policies to deploy ACS "Central" to the hub cluster, and secure any clusters (including hub) that you are managing with ACM.

```
oc apply -k https://github.com/pittar-demos/acm-demo/acm/advanced-cluster-security
```

## DevOps Tooling

Run the following command from the `00-setup` directory to install:
* OpenShift GitOps Operator and default instance
* OpenShift Pipelines Operator
* Noobaa (S3 Storage)
* Quay
* ACM Observability

```
oc apply -k acm
```