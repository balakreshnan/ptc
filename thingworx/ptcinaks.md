# Implement PTC Thingworx in Azure PaaS

## Use Case

### Implement PTC Thingworx Industrial IoT Solution in Azure PaaS

- How to deploy thinkgworx in Azure using PaaS components
- Using AKS for application
- Using Azure SQL database for Database Storage
- Using Azure IoT Hub for device communication and management
- using Azure Storage for checkpoint and long term data storage
- docker containers are stored in Azure container registry
- Store secrets in azure keyvault

## Architecture

![alt text](https://github.com/balakreshnan/ptc/blob/main/images/IoTStrategy.jpg "Service Health")

## Design

- Network design
    - Create a private Network for AKS
    - Create a private endpoint for Storage
    - Create a private endpoint for Azure SQL Database
- Azure firewall
- VM - F16 series VM with 16 CPU - 32 GB - 3 nodes minimum for production

## Azure Components

- IoT Hub 
- Azure SQL Database
    - For Development - DTU - 200 minimum
    - For QA/Test/Production - 16 CPU - 32 Gigs
- Azure Container Registry
- Azure Keyvault
- Azure Storage - ADLS Gen2
- Azure AD
- Azure Monitor
- Azure Devops - for CI/CD Infratstructure deployment

## Thingxworx components

- Development
    - 1 Nginx Controller - ingress docker container
    - 1 thingworx docker container
    - 1 Ignite containers
    - 1 IotHub thingworx connector
    - 1 Zooker nodes

- Production/QA/Test
    - 2 Nginx Controller - ingress docker container
    - 3 thingworx docker container
    - 2 Ignite containers
    - 1 IotHub thingworx connector
    - 3 Zooker nodes
- Above configuration can take upto 100,000 devices
- Assign ngix controller to thingworx URL - Basically match port 443 to nginx ip to thingworx IP.
- Architecture above shows what port it connects to

## How To

- Download the Thingworx modules from PTC's download web site
    - https://support.ptc.com/help/thingworx/platform/r9/en/index.html#page/ThingWorx%2FHelp%2FInstallation%2FThingWorxDockerGuide%2Fthingworx_docker_landing_page.html%23
- Modules downloaded are zip files or jar files
- Create docker image and upload into Azure container registry
- Configure thinkgworx to connect to Azure SQL Database
- Install thingworx container in Kubernetes pod
- Install NGinx container in pod
- Configure the nginx IP to thingworx (This is to access Thingworx URL - https://IP:443/)
- Configure thinkworx container with Azure SQL information
    - This will create the schema when loaded first time
    - Thinkworx uses SQL Authentication
    - Will create a database called thinkworx
- Once configured login into the thingworx URL
- Configure thingworx with ignite ip address and port
- Configure thingworx with Zookeeper ip address and port
- Configure IoT hub connector
    - This is PTC created container
    - Thingworx will create a consumer group called thingworx
    - Configure storage container for checkpoint
    - Configure IoT Hub settings as per PTC documentation
    - https://support.ptc.com/help/thingworx/azure_connector_scm/en/#page/thingworx_scm_azure%2Fazure_connector%2Fc_azure_connector_create_security_entities_for_connector.html%23
    - Connector port is 9009
- Now load and configure all the thinkworx model settings
- Create a new IoT Hub device in the portal
- Configure iot edge device with Iot hub device connection string.
- Configure the edge device to send data to iot hub.
- Log into Thingworx portal and search for the device and see if propertise are updating
- Browse the history and see if new data is available

## Thingworx development

- All development work is done thingworx web portal