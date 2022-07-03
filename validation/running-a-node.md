# Running a Validator Node

Running a validator node requires server based on any linux distributive, installed docker and basic unix shell skills.

### Clone the repo

To get started, you need to clone a repository `https://gitlab.com/chainfusion/cfnode-compose.git`, this project contains directories with different configurations that help to run a node in docker environment. Right after cloning the repo you need to open `validator` directory:

```bash
git clone https://gitlab.com/chainfusion/cfnode-compose.git
cd cfnode-compose/validator
```

### Generate keystore file

A validator needs a key in order to sign blocks, process bridge events and receive a reward. To generate validator key, you need to execute the following command:

```bash
docker run \
    --rm -v $(pwd)/keystore:/data/keystore -it chainfusion/cfnode:latest \
    account new --datadir=/data
```

When generating the key, you will be asked to create new password that will encrypt your generated key. Generated key will be stored in the `keystore/` directory.

Make sure you remember the password you gave when creating a key. Without it you are not able to unlock your account and lose access to validator stake.

### Configure validator node

Copy file `.env.example` as `.env`. In this file you will need to put docker image tag into a `IMAGE` variable, put the password of the generated key into a `ACCOUNT_PWD` variable, put your public address without leading `0x` from generated key into a `ADDRESS` variable. The resulting `.env` file should look like this:

```bash
# Docker image of validator node,
# could be left without changes
IMAGE=chainfusion/cfnode:latest
# List of initial nodes to connect to,
# could be left without changes
BOOTNODES=enode://6295b6ea88a1519b7b0078c9e7d39921cdc73bdca67e029c1675c67076b0ccdcadc51b2f333f1eafab4ea6501afecb1bad7cb7cd4edaf91e5696ee89dce05edb@bootnode.chainfusion.org:30303
# External IP of your machine, where validator is started,
# should be set to be findable by other nodes
EXTERNAL_IP=127.0.0.1
# Public address of generated keystore, without leading 0x,
# could be found inside keystore file
VALIDATOR_ADDRESS=
# Password of keystore file,
# in case you set it during generation,
# otherwise leave empty
VALIDATOR_PASSWORD=
```

### Launch validator node

Now let's launch your validator node in background using `docker-compose` command:

```bash
docker-compose up -d
```

### See validator logs

Last 100 lines of validator logs:

```bash
docker-compose logs --tail=100 -f validator
```

All validator logs:

```bash
docker-compose logs -f validator
```

### Validator Staking

At the last step, after your node is up and running, you can finally stake and become a validator to receive rewards during validation process.

You need to call `stake()` method in [ValidatorStaking](https://explorer.chainfusion.org/address/0x5E85B5Ab4ABfBf7178B1E92AB9df0C1188e839D1) contract. Minimum stake amount is **1000 CFN**, more stake amount increases relative validation rewards in **CFN**.

### Verify that node is producing blocks

In order for you to start validating, you must wait for the new epoch (i.e. validation cycle). If everything went correctly before and the committed stake was sufficient to enter the validator shortlist, your validator node will start to produce blocks in the next validation cycle.
