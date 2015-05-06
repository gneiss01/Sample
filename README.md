Deploy to Azure
===============

> Prequisities:

* You need azure-cli NPM package installed

> Deploy to new VM

* With following command you can deploy to new VM in Azure
*** You can change parameters if required ***

    time azure vm create --custom-data=cloud-config.yaml --ssh=22 --ssh-cert=go-agent-cert.pem  --no-ssh-password --vm-name=ncp-elk-stack-1 --location="West US" --vm-size="Medium" ncp-elk-stack 2b171e93f07c4903bcad35bda10acf22__CoreOS-Stable-607.0.0 ncpadmin


> Enabling end point

    azure vm endpoint create -n Kibana  ncp-elk-stack-1 8080 8080

> Component versions

    Elastic search: 1.5.1
    Logstash:       1.4.2
    Kibana:         4.0.2
    Nginx:          1.9.0
