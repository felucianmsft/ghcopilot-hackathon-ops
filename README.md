# Operations Hackathon 🧑‍💻👩‍💻
Welcome to the Operations Hackathon. The goal is to develop an infrastructure described in the "Goal" section using the most modern development tools: Azure DevOps Repos/Pipeline for code and automation, GitHub Codespaces as development environment and obtaining assistance from GitHub Copilot.

## Codespace Environment 💻
**Installed Software:** Terraform, Azure CLI  
**VS Code Extensions:** GitHub Copilot, Terraform, Azure  
**Azure DevOps Repo:** https://dev.azure.com/hackaton-ops/hackaton-ops

## Start the Hackathon 🏁
1) Collect your GitHub and Azure DevOps credentials from the instructors
2) Click on 'Code -> Select Codespaces tab -> New with options' and select a machine size to start the Codespace
3) Wait for the inizialization of the codespace
4) Select the branch corresponding to your username (i.e. opsuser01)
5) Happy coding 😊

### Terraform Development 
Login to Azure by using Terraform environment variables as shown below (Service Principal authentication):
```
export ARM_CLIENT_ID=$CLIENT_ID
export ARM_CLIENT_SECRET=$SECRET
export ARM_TENANT_ID=$TENANT_ID
export ARM_SUBSCRIPTION_ID=$SUBSCRIPTION_ID
```
Execute terraform commands:
```
terraform init, validate, plan, apply
```

# Challenge: Provision Audiologist App Infrastructure 🕶️
The infrustructure must be created by IaaC in Azure by using Terraform and a storage account for the state. The resources must be deployed in an existing resource group.

The reference architecture for the Azure Infrastructure is composed of:
1. **Azure App Service**: This is a fully managed platform for building, deploying, and scaling web apps. You can use it to host the web application.  
2. **Azure SQL Database**: This is a fully managed relational database with built-in intelligence for high performance. You can use it to store the data collected from the app. The database would hold tables for customers and their respective prescription data. 
3. **Virtual Network and Private Endpoint**: The AppService must reach the the Azure SQL Database over a private network
4. **Azure Front Door**: The application muste be exposed for security and delivery purpose by an Azure Front Door

NOTES:  
Configure a Connection String named "DatabaseConnection" that will be used by the Application for access the database in the App Service.

### GitHub Action
- The infrastructure must be deployed with a GitHub Action

# GitHub Copilot assistance 🤖
Given the infrastructure requirments, try to ask to GitHub Copilot for help, following some suggestions:
<table>
	<tr><th>Requirements</th><th>Ask to GitHub Copilot…</th></tr>
	<tr>
		<td>The infrustructure must be created by IaaC in Azure  and a storage account must be used for the state.</td>
		<td>Generate Terraform file with azure provider and state on storage account</td>
  </tr>
	<tr>
		<td>
      		The resources must be deployed in existing resource group.
		</td>
		<td>
		  Reference an existing resource group
		</td>
	</tr>
	<tr>
		<td>Azure App Service Resource
		</td>
		<td>
		1. Generate code for Azure App Service for .NET App  <br>
		2. Configure a Log Analytics Workspace Based Application Insights for the App Service
		</td>
	</tr>
	<tr>
		<td>
		Azure SQL Database Resource
		</td>
		<td>
		1. Generate code for Azure SQL Database  <br>
		2. Add connection string to Azure SQL as Configuration to the App Service
		</td>
	</tr>
  <tr>
		<td>
		Virtual Netowrk and Private Endpoint
		</td>
		<td>
		1. Add a virtual network <br>
    		2. Connect the App Service to the Azure SQL Database through the virtual network <br>
		3. Add Private DNS Zone for SQL Server to existing VNET <br>
		4. Add record to Private DNS Zone for SQL Server Private Endpdoint IP
		</td>
	</tr>
   <tr>
		<td>
		Azure Front Door
		</td>
		<td>
		1. Add an Azure Front Door that exposes the Azure App Service
		</td>
	</tr>
	 <tr>
		<td>
		    GitHub Action
		</td>
		<td>
		1. Generate a GitHub Action pipeline that deploys the Terraform in Azure
		</td>
	</tr>
</table>

# Solution
An example of solution implemented following the Hackathon instructions can be found in "/solution" folder of this repo. 