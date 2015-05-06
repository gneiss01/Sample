Deploy to Azure
===============

> Prequisities:

* You need azure-cli NPM package installed

> Deploy to new VM

* With following command you can deploy to new VM in Azure
*** You can change parameters if rquired ***

    time azure vm create --custom-data=deploy/cloud-config.yaml --ssh=22 --ssh-cert=myCert.pem  --no-ssh-password --vm-name=ncp-infra-slave-1 --location="Southeast Asia" ncp-infra-slave 2b171e93f07c4903bcad35bda10acf22__CoreOS-Stable-607.0.0 core

> Enabling end point

    azure vm endpoint create -n Interpreter ncp-infra-slave-1 80 80

> Remotely restarting service (using SSH):

    ssh -i private_key ncpadmin@ncp-infra-slave.cloudapp.net systemctl restart interpreter@1.service
