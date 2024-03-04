

Terraform commands to execute the script

```sh
# initialise project & download providers
terraform init

# preview what will be created with apply & see if any errors
terraform plan

# exeucute with preview
terraform apply -var-file terraform.tfvars

# execute without preview
terraform apply -var-file terraform.tfvars -auto-approve

# destroy everything
terraform destroy

# show resources and components from current state
terraform state list
```

#### Get access to EKS cluster
```sh
# install and configure awscli with access creds
aws configure

# check existing clusters list
aws eks list-clusters --region eu-central-1 --output table --query 'clusters'

# check config of specific cluster - VPC config shows whether public access enabled on cluster API endpoint
aws eks describe-cluster --region eu-central-1 --name myapp-eks-cluster --query 'cluster.resourcesVpcConfig'

# create kubeconfig file for cluster in ~/.kube
aws eks update-kubeconfig --region eu-central-1 --name myapp-eks-cluster

# test configuration
kubectl get svc
```


#### reference
```sh
terraform init
terraform plan -var-file terraform.tfvars 
terraform apply -var-file terraform.tfvars 
aws configure
aws eks update-kubeconfig --region us-east-1 --name myapp-eks-cluster
kubectl get nodes
cd kubernetes/
kubectl apply -f config.yaml 
k get pods
kubectl get svc
helm repo add hashicorp https://helm.releases.hashicorp.com
helm install eks hashicorp/consul --version 1.0.0 --values consul-values.yaml --set global.datacenter=eks --namespace satya --create-namespace 
kubectl delete -f config.yaml 
kubectl apply -f config-consul.yaml 
k get pods
cd terraform/
terraform destroy -var-file terraform.tfvars
https://developer.hashicorp.com/consul/docs/k8s/installation/install  
https://github.com/hashicorp/consul-helm/blob/master/values.yaml
```
