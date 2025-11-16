# Databricks

## Databricks Magic Command

| Databricks Magic Command | Description                                              |
| ------------------------ | -------------------------------------------------------- |
| `%config`                | allows you to set configuration options for the notebook |
| `%env`                   | allows you to set environment variables                  |
| `%fs`                    | allows you to interact with the Databricks file system   |
| `%jobs`                  | lists all the running jobs                               |
| `%load`                  | loads the contents of a file into a cell                 |
| `%lsmagic`               | lists all the available magic commands                   |
| `%matplotlib`            | sets up the matplotlib backend                           |
| `%md`                    | allows you to write markdown text                        |
| `%pip`                   | allows you to install Python packages                    |
| `%python`                | switches the notebook context to Python                  |
| `%r`                     | switches the notebook context to R                       |
| `%reload`                | reloads the contents of a module                         |
| `%run`                   | runs a Python file or a notebook                         |
| `%scala`                 | switches the notebook context to Scala                   |
| `%sh`                    | executes shell commands on the cluster nodes             |
| `%sql`                   | allows you to run SQL queries                            |
| `%who`                   | lists all the variables in the current scope             |

- You can use `?` to see documentation of any magic command. For example: `%config?`
- You can use `??` to see code of any magic command. For example: `%config??`

## Databricks Utilities

The following utilities are available via the `dbutils` object:

- `dbutils.credentials`
- `dbutils.data`
- `dbutils.fs`
- `dbutils.jobs`
- `dbutils.library`
- `dbutils.notebook`
- `dbutils.secrets`
- `dbutils.widgets`
- `dbutils.preview`
