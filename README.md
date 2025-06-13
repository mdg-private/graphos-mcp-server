# GraphOS MCP Server PoC

Get a graph key or a user key issued on GraphOS, and start the MCP server as follows:

```sh
$ cargo run -p apollo-mcp-server -- -s graphql/graphos/api.graphql -o graphql/graphos/operations -i -e https://api.apollographql.com/api/graphql --http-address 127.0.0.1 --http-port 5000 --header "apollographql-client-name: mcp" --header "apollographql-client-version: 1.0" --header "X-API-KEY: <Your API Key>"
```

## How to test it with Claude Desktop

Add the `graphos` entry to your Claud Desktop config file:

```json
{
  "mcpServers": {
    "graphos": {
      "command": "<YOUR PATH>/graphos-mcp-server/target/debug/apollo-mcp-server",
      "args": [
        "-s",
        "<YOUR PATH>/graphos-mcp-server/graphql/graphos/api.graphql",
        "-o",
        "<YOUR PATH>/graphos-mcp-server/graphql/graphos/operations", 
        "-e",
        "https://api.apollographql.com/api/graphql",
        "--header",
        "apollographql-client-name: mcp",
        "--header",
        "apollographql-client-version: 1.0",
        "--header",
        "X-API-KEY: <YOUR KEY>"
      ]
    }
  }
}
```

Be sure to replace `<YOUR PATH>` and `<YOUR KEY>`.