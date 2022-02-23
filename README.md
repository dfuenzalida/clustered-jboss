# Clustered JBoss Quickstart

To complete this quickstart you will need an active Azure Subscription and the Azure CLI. If you do not have the Azure CLI installed locally, you can use the [Azure Cloud Shell](https://docs.microsoft.com/azure/cloud-shell/quickstart) in your web browser.

1. Clone this repository

    ```bash
    git clone https://github.com/JasonFreeberg/clustered-jboss.git
    ```

2. Run the shell commands below to create a resource group and deploy the ARM template. The template will create a Virtual Network, App Service Plan, and JBoss EAP web app. The `WEBAPP_NAME` must be globally unique, so consider using your name or appending numbers to ensure it's unique.

    ```bash
    WEBAPP_NAME=<provide a unique name>  # upper and lowercase letters, numbers, and dashes OK
    LOCATION=eastus
    RESOURCE_GROUP=jboss-rg
    az group create --name $RESOURCE_GROUP --location $LOCATION
    az deployment group create \
        --name jboss_deployment \
        --resource-group $RESOURCE_GROUP \
        --template-file arm-template.json \
        --parameters jboss_app_name=${WEBAPP_NAME}
    ```

3. Build the app

    ```bash
    mvn clean package
    ```

4. Deploy the app

    ```bash
    az webapp deploy -n $WEBAPP_NAME -g $RESOURCE_GROUP --src 
    ```

5. Browse to the app. Explain to use the counter and come back to see the new information.


More advanced app:
https://github.com/Azure/rhel-jboss-templates/tree/master/eap-session-replication
