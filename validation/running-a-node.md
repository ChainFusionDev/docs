# Running a Node

Running a node requires server based on any linux distributive, installed docker and basic unix shell skills.

## _Clone Repo_

To get started, you need to clone a repository `https://gitlab.com/chainfusion/cfnode-compose.git`. As a result, you will receive the project in which there will be two folders: *multi-validator* and *single-validator*. You need to log in to *single-validator*. This folder contains the following files:

- *config*
- *.env.example*
- *.gitignore*
- *bootnode-init.sh*
- *docker-compose.yaml*
- *validator-init.sh*

## _Generate Keystore File_

A validator needs a key in order to sign blocks and receive a reward. To generate the key, you need to be in *single-validator* folder and execute the following command:

```sh
docker run --entrypoint="" --rm -v $(pwd):/data -it chainfusion/cfnode:master geth account new --datadir=/data/config/validator
```
When generating the key, you will be asked to come up with a password that will encrypt your generated key. As a result, your generated key will be stored in the * config / validator / keystore * folder.

## _Configure Setup_

Rename file *.env.example* to *.env*. In this file you need set docker image, into IMAGE, write the password to the generated key, into ACCOUNT_PWD, put your public address without leading 0x from generated key, into ADDRESS. The resulting .env file should look like this:

```
IMAGE=chainfusion/cfnode:master
ACCOUNT_PWD=1234
VALIDATOR_ADDRESS=8E9c2a51f072E857ddCdB94bcbd1689098458c04
```

## _Launch Validator Node_
Now launch your validator node using docker-compose file in *single-validator* directory:

```
docker-compose up
```

## _Verify that Node is producing Blocks_
In order for you to start validating, you must wait for the new epoch (i.e. validation cycle). If everything went correctly before and the committed stake was sufficient to enter the validator shortlist, your validator node will start to produce blocks in the next validation cycle.
