# Azure Functions

## Azure Function Core Tools

- Install Core Tools using this [link](https://learn.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=windows%2Cisolated-process%2Cnode-v4%2Cpython-v2%2Chttp-trigger%2Ccontainer-apps&pivots=programming-language-csharp#install-the-azure-functions-core-tools)
- It's recommended to install 64-bit version for VS Code Debugging support
- To create an Azure Functions project, you can use the `func init` command. Here are examples for Python and Go:

**For Python:**

```cmd
func init MyProjFolder --worker-runtime python
```

For Go (which uses custom handlers):

```cmd
func init MyProjFolder --worker-runtime custom
```

In general the command is as follows:

```cmd
func init MyProjFolder --worker-runtime <options>
```

Where `<options>` are `dotnet-isolated`, `dotnet`, `node`, `python`, `powershell`, `custom`

These commands will initialize a new Azure Functions project in the specified folder (MyProjFolder) with the appropriate worker runtime for each language.

Reference : [Link](https://learn.microsoft.com/en-us/azure/azure-functions/functions-core-tools-reference?tabs=v2)
