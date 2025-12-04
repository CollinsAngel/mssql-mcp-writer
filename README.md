# @connorbritain/mssql-mcp-writer

Model Context Protocol server for SQL Server with **read and data operations** - no DDL/schema changes included.

This is the middle tier of the [mssql-mcp-server](https://github.com/ConnorBritain/mssql-mcp-server) family. Use this package when you need both reading and data manipulation but want to prevent schema changes.

## Tools Included (17 tools)

| Category | Tools |
|----------|-------|
| **Discovery** | `search_schema`, `describe_table`, `list_table`, `list_databases`, `list_environments` |
| **Profiling** | `profile_table`, `inspect_relationships`, `inspect_dependencies`, `explain_query` |
| **Data Read** | `read_data` (SELECT only) |
| **Data Write** | `insert_data`, `update_data`, `delete_data` (with preview/confirm) |
| **Scripts** | `list_scripts`, `run_script` |
| **Operations** | `test_connection`, `validate_environment_config` |

## What's NOT included

- `create_table`, `create_index`, `drop_table` - schema/DDL changes

For DDL operations, use [@connorbritain/mssql-mcp-server](https://github.com/ConnorBritain/mssql-mcp-server).
For read-only access, use [@connorbritain/mssql-mcp-reader](https://github.com/ConnorBritain/mssql-mcp-reader).

## Install

```bash
npm install -g @connorbritain/mssql-mcp-writer@latest
# or run directly
npx @connorbritain/mssql-mcp-writer@latest
```

## MCP Client Config

```json
{
  "mcpServers": {
    "mssql": {
      "command": "npx",
      "args": ["@connorbritain/mssql-mcp-writer@latest"],
      "env": {
        "SERVER_NAME": "127.0.0.1",
        "DATABASE_NAME": "mydb",
        "SQL_AUTH_MODE": "sql",
        "SQL_USERNAME": "app_user",
        "SQL_PASSWORD": "YourPassword123"
      }
    }
  }
}
```

## Configuration

| Variable | Required | Notes |
|----------|----------|-------|
| `SERVER_NAME` | Yes | SQL Server hostname/IP |
| `DATABASE_NAME` | Yes | Database to target |
| `SQL_AUTH_MODE` | | `sql`, `windows`, or `aad` (default: `aad`) |
| `SQL_USERNAME` / `SQL_PASSWORD` | | Required for `sql`/`windows` modes |
| `READONLY` | | `true` disables write tools (makes it behave like reader) |
| `ENVIRONMENTS_CONFIG_PATH` | | Path to multi-environment JSON config |
| `SCRIPTS_PATH` | | Path to named SQL scripts directory |

## Package Tiers

| Package | Tools | Use Case |
|---------|-------|----------|
| [mssql-mcp-reader](https://github.com/ConnorBritain/mssql-mcp-reader) | Read-only (14 tools) | Analysts, auditors, safe exploration |
| **mssql-mcp-writer** (this) | Reader + data ops (17 tools) | Data engineers, ETL developers |
| [mssql-mcp-server](https://github.com/ConnorBritain/mssql-mcp-server) | All tools (20 tools) | DBAs, full admin access |

## Documentation

**Full documentation:** [mssql-mcp-server README](https://github.com/ConnorBritain/mssql-mcp-server#readme)

**Issues:** https://github.com/ConnorBritain/mssql-mcp-writer/issues
