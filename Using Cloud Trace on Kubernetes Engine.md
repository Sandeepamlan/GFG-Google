# Using Cloud Trace on Kubernetes Engine GSP484
##  Run in Cloudshell
```cmd
git clone https://github.com/GoogleCloudPlatform/gke-tracing-demo
cd gke-tracing-demo
cd terraform
gcloud config set compute/region us-central1
gcloud config set compute/zone us-central1-a
sed -i '/version = "~> 2.10.0"/d' provider.tf
terraform init
../scripts/generate-tfvars.sh
terraform plan
terraform apply --auto-approve
kubectl apply -f tracing-demo-deployment.yaml
echo http://$(kubectl get svc tracing-demo -n default -o jsonpath='{.status.loadBalancer.ingress[0].ip}')?string=CustomMessage
```
> Click on the link from last line in terminal

>Continue to site  

> If not then check with service and ingress then External Link and Open that link. 
> It Should print ```Hello World!```

# Thank You!
