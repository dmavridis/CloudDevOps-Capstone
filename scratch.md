## Jenkins-X installation
```
apt update
apt upgrade
apt install default-jdk

curl -L https://github.com/jenkins-x/jx/releases/latest/download/jx-linux-amd64.tar.gz | tar xzv
sudo mv jx /usr/local/bin
export PATH=$PATH:~/.jx/bin/

export AWS_ACCESS_KEY_ID=myAccessId
export AWS_SECRET_ACCESS_KEY=mySecret
```

```

jx create cluster eks --cluster-name=dimicloud --domain=dimicloud.co.uk --region us-east-1 --node-type t2.micro --node-volume-size 10 --static-jenkins --tags CreatedBy=JenkinsX  

jx update cluster eks --cluster-name=dimicloud --skip-installation=true --region us-east-1 --node-type t2.nano --node-volume-size 10 --tags CreatedBy=JenkinsX

eksctl create cluster --full-ecr-access --name dimicloud --region us-east-1 --node-type t2.nano --node-volume-size 10 --tags CreatedBy=JenkinsX --aws-api-timeout 20m0s


jx get eks --region us-east-1

jx install --provider=eks --domain=dimicloud.co.uk --default-environment-prefix=dimicloud
export AWS_REGION=us-east-1

https://www.bogotobogo.com/DevOps/Docker/Docker_Kubernetes_Jenkins-X-EKS.php
```

```

```
