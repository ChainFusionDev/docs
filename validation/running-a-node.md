# Running a Node

Running a node requires server based on any linux distributive, installed docker and basic unix shell skills.

### Clone repo

To get started, you need to clone a repository `https://gitlab.com/chainfusion/cfnode-compose.git` to get project with two directories: `multi-validator` and `single-validator`. You need to open `single-validator`.

```bash
git clone https://gitlab.com/chainfusion/cfnode-compose.git
cd single-validator
```

### Generate keystore file

A validator needs a key in order to sign blocks, validate bridge events and receive a reward. To generate the key, you need to be in _single-validator_ folder and execute the following command:

```bash
docker run --entrypoint="" --rm -v $(pwd):/data -it chainfusion/cfnode:master geth account new --datadir=/data/config/validator
```

When generating the key, you will be asked to create new password that will encrypt your generated key. Your generated key will be stored in the `config/validator/keystore/` directory.

### Configure setup

Rename file `.env.example` to `.env`. In this file you need set docker image, into `IMAGE`, write the password to the generated key, into `ACCOUNT_PWD`, put your public address without leading 0x from generated key, into `ADDRESS`. The resulting .env file should look like this:

```bash
IMAGE=chainfusion/cfnode:master
ACCOUNT_PWD=1234
VALIDATOR_ADDRESS=8E9c2a51f072E857ddCdB94bcbd1689098458c04
```

### Launch validator node

Now launch your validator node using docker-compose command in _single-validator_ directory:

```bash
docker-compose up
```

### Verify that node is producing blocks

In order for you to start validating, you must wait for the new epoch (i.e. validation cycle). If everything went correctly before and the committed stake was sufficient to enter the validator shortlist, your validator node will start to produce blocks in the next validation cycle.
