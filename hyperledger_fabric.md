# Hyperledger-Fabric

To deploy Hyperledger Fabric using Docker on Ubuntu, you'll need to follow a series of steps to set up the environment and configure the Fabric network. Here's a high-level overview of the process:

## We will be installing the following:

    1.Git

    2.cURL

    3.Docker and Docker Compose

    4.Go Programming Language

    5.Node.js Runtime and NPM

    6.Python

## Step 1: Create a new USER

It is always a smart idea not to use root to install these softwares. Let us create a new user.

    sudo adduser kakarot

Now we need to add our user to the sudo group.

    sudo usermod -aG sudo kakarot

Switch to our newly created user:

    su - kakarot

## Step 2: Install Prerequisites Install Git, cURL, docker, docker-compose, Node.js , NPM & Pythonsudo 

   

    apt-get update 

    sudo apt-get install git curl docker.io docker-compose nodejs 

    npm python

### Update NPM to 5.6.0 and Configure Docker

    sudo npm install npm@5.6.0 -g 

    sudo usermod -a -G docker $USER 

    sudo systemctl start docker 

    sudo systemctl enable docker

### Install and configure GoLang

    wget https://dl.google.com/go/go1.13.6.linux-amd64.tar.gz 

    tar -xzvf go1.13.6.linux-amd64.tar.gz 

    #Move go to local 

    sudo mv go/ /usr/local

    #Create a new folder go inside home

    cd ~

    mkdir go

    #open .bashrc

    pico ~/.bashrc

    #go to the end of bashrc file and add the following:

    export GOROOT=/usr/local/go 

    export GOPATH= /home/kakarot/go 

    export PATH=$PATH:$GOROOT/bin 

    #replace kakarot with your newly created user

### Log out and Log back as a new user

    exit 

    su - kakarot

## Step 3: Install Hyperledger Fabric Binaries, Docker Containers & Samples

    curl -sSL http://bit.ly/2ysbOFE | bash -s 1.4.4

     #You can replace 1.4.4 with 2.0.0 if you want to install 

    Fabric 2.0.0

You will find a new folder called fabric-samples inside your home folder.

## Step 4: Test the Installation

To make sure that everything works fine we will run a pre-built script called 

“Build Your First Network or BYFN” that will test if you have everything 

installed correctly or not.

    cd fabric-samples/first-network

    ./byfn.sh generate

    ./byfn.sh up

You should get something like below at the end of execution if everything went right. If not you may have made a mistake in the installation process.

    ========= All GOOD, BYFN execution completed ===========

    _____   _   _   ____    

    | ____| | \ | | |  _ \

    |  _|   |  \| | | | | |

    | |___  | |\  | | |_| |

    |_____| |_| \_| |____/

### Check if all the docker containers are running:

    

    docker ps -a

### Clean the Network

    ./byfn.sh down

    

Congratulations! You have successfully installed Hyperledger Fabric in your machine.

