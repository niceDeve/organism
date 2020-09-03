# BLOCKOTUS Organism

What you are looking at is the frame for the best upgrade ever for the civilization privilege escalation game, solved with our intrusion, intelligence and coordination capacities.

Take a seat, the recipe, and start cooking.

## Recipe

### Ingredients

- NVM, node 10 and 12
- Docker (daemon must be running)
- Blockotus Organism

### Steps

Start docker.

Add the following to your .bashrc or .zshrc

```
export BLOCKOTUS=PATH TO YOUR BLOCKOTUS ORGANISM
export PATH=${BLOCKOTUS}/network/bin:$PATH
export FABRIC_CFG_PATH=${BLOCKOTUS}/network/config/

# Environment variables for Org1

export CORE_PEER_TLS_ENABLED=true
export CORE_PEER_LOCALMSPID="Org1MSP"
export CORE_PEER_TLS_ROOTCERT_FILE=${BLOCKOTUS}/network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt
export CORE_PEER_MSPCONFIGPATH=${BLOCKOTUS}/network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp
export CORE_PEER_ADDRESS=localhost:7051

# Environment variables for Org2

export CORE_PEER_TLS_ENABLED=true
export CORE_PEER_LOCALMSPID="Org2MSP"
export CORE_PEER_TLS_ROOTCERT_FILE=${BLOCKOTUS}/network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt
export CORE_PEER_MSPCONFIGPATH=${BLOCKOTUS}/network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp
export CORE_PEER_ADDRESS=localhost:9051
```

Run the following commands from the Organism root directory:

```bash
$ git submodules update --init --recursive
$ yarn run devInstall # you may have to run the command two times and switch your node version
``` 

Done.

## Usage

### Run the complete organism

```bash
$ yarn run dev
``` 

Done.
It executes the following tasks:
- run the Hyperledger network
- deploy chaincode contracts
- start the nerves server
- start the webapp

### Hot Chaincode Contract Upgrade

Assuming you made modifications on the `user` chaincode contracts (User, Keypair or another contract of this organ), and you want it to be deployed to the Network, run:

```bash
$ yarn run upgrade-organ user
``` 

The newly deployed contract will be automatically used by the the organism.

### Accessing to the webapp

Go to http://localhost:5000

### Accessing to the CouchDB database interface

Go to http://localhost:5984/_utils

Credentials: admin / adminpw

### Inspect Chaincode contracts logs (while running)

```bash
$ docker ps # find the container id of the Chaincode you want to inspect
$ docker logs -f <containerId>
```
