# GraphOS MCP Server

Get a graph key or a user key issued on GraphOS, and start the MCP server as follows:

```sh
$ cargo run -p apollo-mcp-server -- -s graphql/graphos/api.graphql -o graphql/graphos/operations -e https://api.apollographql.com/api/graphql --http-address 127.0.0.1 --http-port 5000 --header "apollographql-client-name: mcp" --header "apollographql-client-version: 1.0" --header "X-API-KEY: <Your API Key>"
```
