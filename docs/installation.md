## Installation

### Requirements

- NVM, node 12, 14 and 15
- Docker (daemon must be running)
- Clone this repository

#### Known issue
- macOS: Docker Desktop 2.4.0.0 requires to uncheck "Use gRPC FUSE for file sharing" in Docker -> Preferences -> General

### Steps

Start docker.

Run the following commands from the Organism root directory:

```bash
$ yarn run update-submodules
$ bash scripts/install.sh [--skip-binaries]
``` 

Done.
