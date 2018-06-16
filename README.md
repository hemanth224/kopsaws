# kopsaws

Prerequisites:

Install Kops

Install Kubectl

Install AWS CLI with Access keys & Secret keys

Create a Bucket

Create a hosted zone in AWS for service discovery for kubernetes



dns in aws:

aws s3 mb s3://cluster5.k8s.appychip.vpc

kops create cluster --name=dev.qlikuse.com --state=s3://cluster5.k8s.appychip.vpc --zones=eu-west-1a --node-count=1 --node-size=t2.micro --master-size=t2.micro --dns-zone=qlikuse.com


kops create cluster --name=qa.qlikuse.com --state=s3://cluster6.k8s.appychip.vpc --zones=eu-west-1a --node-count=1 --node-size=t2.micro --master-size=t2.micro --dns-zone=qlikuse.com

pods info:

kubectl get pods --all-namespaces

delete a cluster:

kops delete cluster --name=qa.qlikuse.com --state=s3://cluster6.k8s.appychip.vpc --yes

kops delete cluster --name=dev.qlikuse.com --state=s3://cluster5.k8s.appychip.vpc --yes


shifting cluster:


https://kubernetes.io/docs/reference/kubectl/cheatsheet/

    username: admin
vagrant@ubuntu-xenial:~$ kubectl config use-context dev.qlikuse.com

Switched to context "dev.qlikuse.com".


To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

vagrant@ubuntu-xenial:~$ kubectl config use-context qa.qlikuse.com

Switched to context "qa.qlikuse.com".

vagrant@ubuntu-xenial:~$ kubectl cluster-info

Kubernetes master is running at https://api.qa.qlikuse.com

KubeDNS is running at https://api.qa.qlikuse.com/api/v1/proxy/namespaces/kube-system/services/kube-dns


To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

vagrant@ubuntu-xenial:~$ kubectl config current-context

qa.qlikuse.com

