## Usage

### Run the complete organism

```bash
# It could take up to 10 minutes: 1min for the network, and another 5 to 10min for contracts.
$ nvm use 14
$ yarn run dev [--skip-network|--skip-contracts|--skip-bootstrap|--skip-nerves|--skip-webapp|skip-all|--run-nerves|...]
``` 

Done.
It executes the following tasks:
- run the Hyperledger network
- deploy chaincode contracts
- start the nerves server
- start the webapp
- run the bootstrap

### Hot Chaincode Contract Upgrade

Assuming you made modifications on the `user` chaincode contracts (User, Keypair or another contract of this organ), and you want it to be deployed to the Network, run:

```bash
$ yarn run upgrade-organ user
``` 

The newly deployed contract will be automatically used by the the organism.

### Accessing to the webapp

Go to http://localhost:4201

### Accessing to the CouchDB database interface

Go to http://localhost:5984/_utils

Credentials: admin / adminpw

### Tests

For a full coverage, start the organism before running tests.

```bash
$ yarn dev
$ yarn test
```

### Inspect Chaincode contracts logs (while running)

```bash
$ docker ps # find the container id of the Chaincode you want to inspect
$ docker logs -f <containerId>
```
