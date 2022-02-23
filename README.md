# Clustered JBoss

1. Clone this repository
1. Run the shell commands below to create a resource group and deploy the ARM template. The template will create a Virtual Network, App Service Plan, and JBoss EAP web app. The `WEBAPP_NAME` must be globally unique, so consider using your name or appending numbers to ensure it's unique.

    ```bash
    WEBAPP_NAME=<provide a unique name>  # upper and lowercase letters, numbers, and dashes OK
    LOCATION=eastus
    RESOURCE_GROUP=jboss-rg
    az group create --name $RESOURCE_GROUP --location $LOCATION
    az deployment group create \
        --name ase_deployment \
        --resource-group $RESOURCE_GROUP \
        --template-uri https://raw.githubusercontent.com/ \
        --parameters webAppName=${WEBAPP_NAME}
    ```

1. Build the app
2. Deploy the app
3. Browse to the app. Explain to use the counter and come back to see the new information.


More advanced app:
https://github.com/Azure/rhel-jboss-templates/tree/master/eap-session-replication
