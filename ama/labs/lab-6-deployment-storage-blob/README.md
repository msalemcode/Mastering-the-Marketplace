# Lab 2 - The Managed Application Deployment Package

In this lab, you will edit the artifacts that go into a an Azure Managed Application deployment package. You will run your artifacts through a validation process and package them for use in deployment. Finally, you will create a new plan for your existing offer from [Lab 1](../lab-1-partner-center/README.md) and publish your offer.

## Exercise 1 - ARM TTK

This exercise introduces **Azure Resource Manager Template Toolkit** (ARM TTK), a tool that runs in PowerShell and validates the artifacts in your deployment package. The ARM TTK tool runs tests that ensure valid `mainTemplate.json` and `createUiDefinition ` files.

You will clone the ARM TTK repository and bring the code to your local machine where it can be executed using PowerShell. 

If you are not on Windows, you may download PowerShell for your platform.

- [Linux](https://github.com/Azure/arm-ttk/blob/master/arm-ttk/README.md#running-tests-on-linux)
- [macOS](https://github.com/Azure/arm-ttk/blob/master/arm-ttk/README.md#running-tests-on-macos)

1. Clone the [ARM TTK repository](https://github.com/Azure/arm-ttk) from GitHub.
2. Set up ARM TTK to run on your machine by executing the following commands in a PowerShell terminal.

> ```powershell
> cd "<PATH TO ARM TTK REPO>\arm-ttk\arm-ttk"
> 
> Import-Module .\arm-ttk.psd1
> ```

3. From the same directory you may execute the **ARM TTK** tool as shown below. Note the path is looking at the `end` folder, which contains the solution to this lab.

```powershell
$AMAPackage = "<PATH TO AMA-WORKSHOP>\ama-workshop\lab-6-deployment-storage-blob\"

Test-AzTemplate -TemplatePath $AMAPackage
```

4. See that test pass. The output from ARM TTK should look something like this.

```
Validating end\createUiDefinition.json
  AllFiles
    [+] JSONFiles Should Be Valid (61 ms)
  CreateUIDefinition
    [+] Allowed Values Should Actually Be Allowed (190 ms)

    ...

Validating end\mainTemplate.json
  deploymentTemplate
    [+] adminUsername Should Not Be A Literal (90 ms)
    [+] apiVersions Should Be Recent In Reference Functions (171 ms)

    ...
```



