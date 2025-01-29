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
