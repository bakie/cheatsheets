## Azure

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

#### Az graph API
Return the directory objects specified in a list of IDs (e.g. ID of a service principal)
```powershell
az rest --method POST --url 'https://graph.microsoft.com/v1.0/directoryObjects/getByIds' --headers 'Content-Type=application/json' --body '{ \"ids\":[\"{ID}\"]}'
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
