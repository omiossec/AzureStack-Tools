# Azure Stack Service Administration

Instructions below are relative to the .\ServiceAdmin folder of the [AzureStack-Tools repo](..\).

Make sure you have the following module prerequisites installed:

```powershell
Install-Module -Name 'AzureRm.Bootstrapper' -Scope CurrentUser
Install-AzureRmProfile -profile '2017-03-09-profile' -Force -Scope CurrentUser
Install-Module -Name AzureStack -RequiredVersion 1.2.9 -Scope CurrentUser
```

Then make sure the following modules are imported:

```powershell
Import-Module ..\Connect\AzureStack.Connect.psm1
Import-Module .\AzureStack.ServiceAdmin.psm1
```

You will need to reference your Azure Stack Administrator environment. To create an administrator environment use the below. The ARM endpoint below is the administrator default for a one-node environment.

```powershell
Add-AzsEnvironment -Name "AzureStackAdmin" -ArmEndpoint "https://adminmanagement.local.azurestack.external" 
```


## Create default plan and quota for tenants

```powershell
Add-AzsTenantOfferAndQuota
```

Tenants can now see the "default" offer available to them and can subscribe to it. The offer includes unlimited compute, network, storage and key vault usage.
