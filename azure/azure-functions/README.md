# Azure Functions

## Azure Function Core Tools

- Install Core Tools using this [link](https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=windows%2Cisolated-process%2Cnode-v4%2Cpython-v2%2Chttp-trigger%2Ccontainer-apps&pivots=programming-language-csharp#install-the-azure-functions-core-tools)
- It's recommended to install 64-bit version for VS Code Debugging support
- To create an Azure Functions project for Python and Go, you can use the following commands:

```cmd
func init MyProjFolder --worker-runtime python
```

```cmd
func init MyProjFolder --worker-runtime <options>
```

`Options` are `dotnet-isolated`, `dotnet`, `node`, `python`, `powershell`, `custom`

These commands will initialize a new Azure Functions project in the specified folder (MyProjFolder) with the appropriate worker runtime for each language.

Reference : [Link](https://learn.microsoft.com/en-us/azure/azure-functions/functions-core-tools-reference?tabs=v2)
