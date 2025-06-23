# GraphOS MCP Server PoC

Get a graph key or a user key issued on GraphOS, and start the MCP server as follows:

## Run it using local operations

The operations are located in the `graphql/graphos` directory of the repository.

```sh
$ cargo run -p apollo-mcp-server -- \
  -o graphql/graphos/operations \
  -s graphql/graphos/api.graphql \
  -e https://api.apollographql.com/api/graphql \
  --http-port 5000 \
  --header "apollographql-client-name: mcp" \
  --header "apollographql-client-version: 1.0" \
  --header "X-API-KEY: 🔑"
```

## Run it using operation collection on Studio

You need to set the `APOLLO_KEY` environment and the `--collection` flag.

```sh
$ APOLLO_KEY=🔒 \
  cargo run -p apollo-mcp-server -- \
  --collection f49cd64f-007d-49b1-87ee-f94555497619 \
  -s graphql/graphos/api.graphql \
  -e https://api.apollographql.com/api/graphql \
  --http-port 5000 \
  --header "apollographql-client-name: mcp" \
  --header "apollographql-client-version: 1.0" \
  --header "X-API-KEY: 🔑"
```

## Test it with Claude Desktop

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
