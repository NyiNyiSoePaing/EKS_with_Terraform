# Getting Started with Amazon EKS using Terraform

More resources:

Terraform provider for AWS [here](https://www.terraform.io/docs/providers/aws/index.html) <br/>


# Pre Requirements
- Terraform CLI 
- AWS CLI

## Terraform CLI 

```
# Get Terraform

curl -o /tmp/terraform.zip -LO https://releases.hashicorp.com/terraform/0.13.1/terraform_0.13.1_linux_amd64.zip
unzip /tmp/terraform.zip
chmod +x terraform && mv terraform /usr/local/bin/
terraform
```

## Amazon CLI

You can get the Amazon CLI on [it.](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html) 
<br/>
We'll need the Amazon CLI to gather information so we can build our Terraform file.


## Login to Amazon

```
# Access your "My Security Credentials" section in your profile. 
# Create an access key

aws configure

Default region name: ap-southeast-1
Default output format: json
```



## Terraform Amazon Kubernetes Provider 

Documentation on all the Kubernetes fields for terraform [here](https://www.terraform.io/docs/providers/aws/r/eks_cluster.html)

```
cd ./terraform

terraform init

terraform plan
terraform apply

```

## Lets see what we deployed

```
# grab our EKS config
aws eks update-kubeconfig --name getting-started-eks --region ap-southeast-1

# Get kubectl

curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
mv ./kubectl /usr/local/bin/kubectl

kubectl get nodes
kubectl get deploy
kubectl get pods
kubectl get svc
```

## Deploy simple deploynment on EKS

```
cd ./simple_deployments
kubectl apply -f nginx.yml
kubectl apply -f nginx-service.yml
kubectl get pod
kubectl get svc

```

# Clean up 

```
terraform destroy
```