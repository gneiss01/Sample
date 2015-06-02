Deploy to Azure
===============

> Prequisities:

* You need azure-cli NPM package installed

> Deploy to new VM

* With following command you can deploy to new VM in Azure
*** You can change parameters if required ***

    time azure vm create --vm-name=ncp-logstash-1 --ssh=22 --custom-data=cloud-config.yaml --ssh-cert=go-agent-cert.pem --no-ssh-password --location="West US" --vm-size="Small" --virtual-network-name=elk-stack-vnet --subscription="Test Salto" --connect ncp-logstash 2b171e93f07c4903bcad35bda10acf22__CoreOS-Stable-607.0.0 ncpadmin

*** Create Internal Load Balancer ***

    azure service internal-load-balancer add -t subnet-2 ncp-logstash logstash-ilb

*** Generate cert/key ***

    openssl req -x509 -batch -nodes -newkey rsa:2048 -keyout logstash-forwarder.key -out logstash-forwarder.crt -subj /CN=ncp-logstash-cluster.cloudapp.net

*** Test Logstash  ***
    docker pull ec2-54-169-239-164.ap-southeast-1.compute.amazonaws.com:5000/lumberjack-docker
    Update logstash forwarder configuration to use the same cert as logstash.

 > Tools version

    Logstash 1.4.2

