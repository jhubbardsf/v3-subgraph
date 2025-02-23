# Uniswap V3 Subgraph

### Subgraph Endpoint

Synced at: https://thegraph.com/hosted-service/subgraph/ianlapham/uniswap-v3-subgraph?selected=playground

Pending Changes at same URL

### Rift Local Devnet Deployment

1. `yarn install`
2. `npm i -g @graphprotocol/graph-cli # Or use your preferred package manager`
3. `graph codegen --output-dir src/types/`
4. `graph create uniswap/uniswap-v3 --node http://127.0.0.1:8020`
5. `graph deploy uniswap/uniswap-v3 --ipfs http://localhost:5001 --node http://127.0.0.1:8020 --version-label=v0.0.1`

TODO: Look into adding local to networks.json

### Running Unit Tests

1. Install [Docker](https://docs.docker.com/get-docker/) if you don't have it already
2. Install postgres: `brew install postgresql`
3. `yarn run build:docker`
4. `yarn run test`

### Adding New Chains

1. Create a new subgraph config in `src/utils/chains.ts`. This will require adding a new `<NETWORK_NAME>_NETWORK_NAME` const for the corresponding network.
2. Add a new entry in `networks.json` for the new chain. The network name should be derived from the CLI Name in The Graph's [supported networks documenation](https://thegraph.com/docs/en/developing/supported-networks/). The factory address can be derived from Uniswap's [deployments documentation](https://docs.uniswap.org/contracts/v3/reference/deployments/ethereum-deployments).
3. To deploy to Alchemy, run the following command:

```
yarn run deploy:alchemy --
  <SUBGRAPH_NAME>
  --version-label <VERSION_LABEL>
  --deploy-key <DEPLOYMENT_KEY>
  --network <NETWORK_NAME>
```
