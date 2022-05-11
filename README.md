# Azure-Standard-LoadBalancer-using-Portal
Create Azure Standard Load Balancer using Portal

Step-00: Usecase Introduction

Create a Simple VNet with two Azure Linux VMs by provisioning sample webserver
Front these VMs with a Azure Standard Load Balancer
Over the proces learn the following load balancer concepts
Frontend IPs
Backend Pools
Health Probes
Load Balancing Rules
Inbound NAT Rules
Verify the same via browser
Implement Inbount NAT rules via LB and connect to VMs using SSH

Step-01: Create two Azure VMs in a Virtual Network

Create Resource Group: slb-demo
Create Virtual Network: vnet1
VM Names: vm1, vm2
Custom Data: app-scripts/redhat-webvm-script.sh

Step-02: Create Azure Standard Load Balancer

Create Load Balancer with atleast one Frontend IP
Create Backend Pool in LB
Create Health Probe
Create Load Balancing Rule
Create Two Inbound NAT Rules

Step-03: Test by accessing the Application

# Curl Test 
curl http://<LB-Public-IP>

# Browser Test
http://<LB-Public-IP>
Step-04: Inbout NAT Rules Test

# SSH Test to VM1
ssh -i manual-lb.pem -p 1022 azureuser@<LB-Public-IP>

# SSH Test to VM2
ssh -i manual-lb.pem -p 2022 azureuser@<LB-Public-IP>
Step-05: Outbound Rules

# SSH Test to VM1
ssh -i manual-lb.pem -p 1022 azureuser@<LB-Public-IP>

# Apache Bench Testing
ab -t 240 -n 100000 -c 100 http://<LB-Public-IP>/index.html
ab -t 240 -n 100000 -c 100 http://40.121.55.137/index.html
-t Time it need to run
-n Number of Requests
-c concurrency
