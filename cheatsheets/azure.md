## Azure

### Az cli
#### Authentication
```bash
az login

## If your account is associated with more than one tenant, sign-in requires the Tenant parameter to be specified when connecting.
az login --tenant {tenantId}
```

Get a list of subscriptions
```bash
az account list
```

Get details of current subscription
```bash
az account show
```

Switch active subscription
```bash
az account set --subscription {subscription_name}
```

Trigger policy scan
```bash
## Trigger a policy compliance evaluation at the current subscription scope.
az policy state trigger-scan

## Trigger a policy compliance evaluation for a resource group.
az policy state trigger-scan --resource-group "{RG}"

## Trigger a policy compliance evaluation for a resource group without waiting for completion.
az policy state trigger-scan --resource-group "{RG}" --no-wait
```

### Az graph API
Return the directory objects specified in a list of IDs (e.g. ID of a service principal)
```bash
az rest --method POST --url 'https://graph.microsoft.com/v1.0/directoryObjects/getByIds' --headers 'Content-Type=application/json' --body '{ \"ids\":[\"{ID}\"]}'
```

### Az PowerShell Module
```powershell
import-module Az
```

#### Authentication
```powershell
connect-azaccount

## If your account is associated with more than one tenant, sign-in requires the Tenant parameter to be specified when connecting.
connect-azaccount -tenant {tenantId}

## This way sometimes gets around MFA restrictions (not always!)
$credential = get-credential
connect-azaccount -credential $credential
```

### EnterprisePolicyAsCode PowerShell Module
```powershell
import-module enterprisepolicyascode
```

#### Authentication
```powershell
connect-azaccount
```

Build the deployment plans
```powershell
build-deploymentplans
```

Deploy policy resources from a plan file
```powershell
deploy-policyplan
```

Deploy role assignments from a plan file
```powershell
deploy-rolesplan
```
