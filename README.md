## Step 1: Create a new USER
- It is always a smart idea not to use root to install these softwares. Let us create a new user.
```sh
sudo adduser <username>
```
- Now we need to add our user to the sudo group.
```sh
sudo usermod -aG sudo <username>
```
- Switch to our newly created user:
```sh
su <username>
```
- Test the sudo access
```sh
sudo ls
```
## Step 2: Install Prerequisites
- Install Git, cURL, Docker and Docker-compose.
Step 1: Install curl, git,Docker and Docker Compose.
Install the latest version of git and curl if it is not already installed.
```sh
sudo apt-get install git curl docker-compose -y
```
Once installed, confirm that the latest versions of all.

```sh
git --version
```
```sh
curl --version
```
```sh
docker --version
```
```sh
docker-compose --version
```

- Make sure the Docker daemon is running.
```sh
sudo systemctl start docker
```
Optional: If you want the Docker daemon to start when the system starts, use the following:
```sh
sudo systemctl enable docker
```
Add your user to the Docker group.
```sh
sudo usermod -a -G docker <username>
```
- Install Golang
```sh
curl -O https://dl.google.com/go/go1.18.3.linux-amd64.tar.gz
```
```sh
tar xvf go1.18.3.linux-amd64.tar.gz
```
```sh
export GOPATH=$HOME/go
```
```sh
export PATH=$PATH:$GOPATH/bin
```
Now, you have to open and edit you **bashrc **file. In most cases, the bashrc is a hidden file that lives in your home directory.

```sh
nano ~/.bashrc
```

Step 3: Install Hyperledger Fabric Binaries, Docker Containers & Samples
Step 4: Test the Installation
Create new directory where you will install Hyperledger Fabric

mkdir fabric-network

Step 4: Install Hyperledger Fabric
To download a specific release, pass a version identifier for Fabric and Fabric CA Docker images. The command below demonstrates how to download the latest production releases - Fabric v2.4.4 and Fabric CA v1.5.3

curl -sSL https://bit.ly/2ysbOFE | bash -s -- <fabric_version> <fabric-ca_version>

curl -sSL https://bit.ly/2ysbOFE | bash -s -- 2.4.4 1.5.3

Download the latest release of Fabric samples, docker images, and binaries.

curl -sSL https://bit.ly/2ysbOFE | bash -s

Congrats, you have installed Hyperledger Fabric with all dependencies.

To test the our installation, we will run test network that comes with fabric-samples

cd fabric-samples/test-network
./network.sh up createChannel -ca -c mychannel -s couchdb

The above command will create a channel(mychannel) with certificate Authorities and bring up couch-db as state database.

Using following Docker command we can check all running containers

docker ps -a

You should be able to see the containers up and running.