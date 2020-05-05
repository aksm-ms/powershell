# Github action for Azure PowerShell
This repository contains Github action for Azure PowerShell to automate your github workflows using Azure PowerShell scripts.

Get started today with a [free Azure account](https://azure.com/free/open-source)!

The definition of this Github Action is in [action.yml](https://github.com/azure/powershell/blob/master/action.yml).

## End-to-End Sample Workflows

### Dependencies on other Github Actions

Login to Azure before running Azure PowerShell scripts using [Azure Login](https://github.com/Azure/login).

```yaml
on: [push]

name: AzurePowerShellSample

jobs:

  build:
    runs-on: ubuntu-latest
    steps:
    
    - uses: azure/login@v1.1
      with:
        creds: ${{secrets.AZURE_CREDENTIALS}}
        enable-AzPSSession: true
        
    - run: |
        az webapp list --query "[?state=='Running']"
        
   
    - uses: azure/powershell@v1
      with:
        inlineScript: |
          Get-AzVM -ResourceGroupName "ResourceGroup11"
        azPSVersion: 'latest'
```

# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
