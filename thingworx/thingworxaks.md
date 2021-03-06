# Run Thingworx in Azure Kubernetes Service + IoT Hub

## Use Case

- Run Thingworx industrial iot platform in AKS cluster
- run Thingworx in PaaS
- Ability to scale as needed
- Use Azure SQL PaaS as back end
- Use other dependant PaaS services
- Data ingestion using IoT hub

## Requirements

- Docker installed in local laptop
- helm installation
- Azure account
- Create a Resource Group
- Get Thingworx docker scripts
- Get Iot hub connector docker scripts
- Get nginx helm charts
- Get thinkgworx, iot hub connector help charts

## Architecture

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/IoTStrategy.jpg "Service Health")

## Process

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/ptcthingworxprocess.jpg "Service Health")

## Steps

- Create a Azure Resource Group
- Create New Azure SQL using scripts from thingworx
- Create a storage account
- Create IoT Hub and a Storage for routing messages
- Create Azure container services
- Create Key vault
- Create AKS cluster and it's dependant configuration and services
- Now Create a AKS cluster
- cluster created in private VNET
- Create the load balancer
- Create VM's for Pod
- Make sure scaling is available to up and down
- Down load the scripts from Thingworx to build the docker container for
    - Thingworx container
    - Iot Hub connector container
- Save the container in Container registry
- Configure the AKS to deploy thinkgworx container
- Enable admin login with Azure container services
- Get secret to login into container registry to pull images
- Get secret
- Thingworx helm chart config
- Push container
- Create schema for sql
- Download container for thingworx
- Follow the below instruction to create thinkworx docker container
- Need to download feature files and then create a docker container

https://support.ptc.com/help/thingworx/platform/r9/en/index.html#page/ThingWorx%2FHelp%2FInstallation%2FThingWorxDockerGuide%2Fthingworx_docker_landing_page.html%23

- Configure public IP for thingworx
- Configure the container with sql connection
- Install licence
- Basic load balancer
- Download NGinx helm chart from web
- Download and install dependencies before install nginx
- install nginx controller
- ingress controller secret
- Create a  new secret file

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/nginxsecret1.jpg "Service Health")

- ingress controller config

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/ingressconfig1.jpg "Service Health")

- Values cert config

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/valuescert.jpg "Service Health")
![alt text](https://github.com/balakreshnan/ptc/blob/main/images/valuescert1.jpg "Service Health")
![alt text](https://github.com/balakreshnan/ptc/blob/main/images/valuescert2.jpg "Service Health")

- Nginx controller - running in SSL with port 443

- Configure thinkworx
- thingworx secret file

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/thinkgworxsecret.jpg "Service Health")

- Download Extentions from thingworx web site
- Import iot hub extension
- Configure iot hub connector

https://support.ptc.com/help/thingworx/azure_connector_scm/en/#page/thingworx_scm_azure%2Fazure_connector%2Fc_azure_connector_create_security_entities_for_connector.html%23

- Download and install iot hub container
- Need user, group, organization, entities and permission
- Create a application key to be used for connector
- Configure the connector
- Get iot hub connection string from azure protal
- list of all the containers

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/ptc6.jpg "Service Health")

- iot hub connector configured

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/ptc2.jpg "Service Health")

- iot out of healthy iot hub connector

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/ptc3.jpg "Service Health")

- Download demo application
- Unzip the application
- Import into thingworx
- Thingworx can be accessed in port 80 with public IP and dns name
- All configuration is done through the thingworx UI for application specific
- All the infra will be created as code and deployed
- Sample devices are created
- start the demo application in cloud shell using node start.js
- watch the data getting updated in thingworx and iot hub

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/ptc4.jpg "Service Health")