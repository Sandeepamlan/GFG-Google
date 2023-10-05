# Cloud Monitoring: Qwik Start GSP089
# Run in cloudshell
> Copy Zone name from Task 1
```cmd
export ZONE=
```
```cmd
gcloud compute instances create lamp-1-vm \
--zone=$ZONE \
--machine-type=e2-medium \
--image-project=debian-cloud \
--image-family=debian-11 \
--tags=http-server
gcloud compute firewall-rules create allow-http \
--action=ALLOW \
--direction=INGRESS \
--rules=tcp:80 \
--source-ranges=0.0.0.0/0 \
--target-tags=http-server
gcloud compute ssh lamp-1-vm --zone=$ZONE
```
```cmd
sudo apt-get update
sudo apt-get install apache2 php7.0
sudo service apache2 restart
curl -sSO https://dl.google.com/cloudagents/add-google-cloud-ops-agent-repo.sh
sudo bash add-google-cloud-ops-agent-repo.sh --also-install
sudo apt-get update
```
> Please do ```Create an uptime check``` and ```Create an alerting policy```.
