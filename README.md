# vindinium-docker
Dockerfile for vindinium-docker image and deployment to AWS (2 Nodes, 1 for Vindinium and another for MongoDB)

## Running locally
You will need to run a mongo container first:

1. docker run --name mongo mongo

Then you can run the vindinium container:

1. docker run -i --link mongo:mongo -p 9000:9000 --name vindinium jamesmmchugh/vindinium-docker
3. Ctrl+D to exit

## Running in AWS

### Pre-Requisites

1. You need to install the AWS CLI on your computer (https://aws.amazon.com/cli/)
2. You need an AWS Account and access to a Secret Key
3. Add your secret to the project directory (Call it the same as what is referenced in ansible.cfg)
4. Update group_vars/all.yml to include your Access/Secret AWS keys
5. Ensure you have a security group called "vindinium" on AWS. This group should have a security rule for MongoDB on TCP port 27017/18
6. Note that you will have to manually terminate instances from the AWS dashboard after use

### Deployment

1. ./aws.sh create
2. ./aws.sh deploy

Linked to an auto-build @ https://hub.docker.com/r/jamesmmchugh/vindinium-docker/
