## Jenkins-X installation
```
apt update
apt upgrade
apt install default-jdk
```

jx create cluster eks --cluster-name=dimi-cloud --skip-installation=true

eksctl create cluster --full-ecr-access --name dimi-cloud --region us-west-2 --node-type t2.nano --node-volume-size 8 --tags CreatedBy=JenkinsX --aws-api-timeout 20m0s

jx install --provider=eks --domain=konsek.cloud --default-environment-prefix=konsek-cloud
