### Encrypted Secrets testing container

This container has all the tools needed to test blackbox enabled repositories.

To get started, build the container:

    docker build -t iflowfor8hours/blackbox-container .

And then run the container

    docker run -u root -it iflowfor8hours/blackbox-container /bin/bash

Add the private ssh key that is associated with your github account to ~/.ssh/id_rsa so you can clone private repos.

    # Copy it from your host machine
    cat ~/.ssh/id_rsa | pbcopy
    # Paste into the container default ssh config
    vim ~/.ssh/id_rsa
    chmod 600 ~/.ssh/id_rsa
    git config --global user.name "Paranoid Psychonaut"
    git config --global user.email "paranoid@psychonaut.co.uk"

To access credstash, your AWS credentials need to be in the environment. Copy them from your environment and export them to the container. Execute the following commands to accomplish this.

    # Copy it from your host machine
    cat ~/.aws/credentials|pbcopy
    # Export them into the container
    export AWS_REGION=us-east-1
    export AWS_ACCESS_KEY_ID=
    export AWS_SECRET_ACCESS_KEY=

Clone a repository and follow the instructions in SECRETS.md for information on how to manipulate the secrets of that particular application.
