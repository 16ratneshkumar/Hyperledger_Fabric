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
### Curl Installation
- Run below command to install Curl.
```sh
sudo apt-get install curl
```  
- Verify the installation and check the version of Curl using below command.
```sh 
curl --version
```

### Git Installation
- Open the ubuntu terminal and run below command. This will start the installation for Git.
```sh	 
sudo apt-get install git
```	 
- Run below command to check if Git is successfully installed or not. This should return the version of Git.
```sh	 
git --version
```

### [Nodejs Installation](https://github.com/16ratneshkumar/1_Year/blob/main/2_Semester/Computer%20Science/Blockchain/how%20to%20install%20node%20js.md)
### Docker Installation
- Install the latest version of Docker if it is not already installed.
```sh
sudo apt-get -y install docker-compose
```
-  Run below command to check if docker and Docker Compose is successfully installed or not. This should return the version of it.
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

- **Optional: If you want the Docker daemon to start when the system starts, use the following:**
```sh
sudo systemctl enable docker
```

- Add your user to the Docker group.
```sh
sudo usermod -a -G docker <username>
```
### Go Installation
- Run below command to install golang package.
```sh
curl -O https://dl.google.com/go/go1.18.3.linux-amd64.tar.gz
```
- Extract the package.
```sh
tar xvf go1.18.3.linux-amd64.tar.gz
```
- Set the GOPATH
```sh
export GOPATH=$HOME/go
```
```sh
export PATH=$PATH:$GOPATH/bin
```
-  Run below command to check if docker and Docker Compose is successfully installed or not. This should return the version of it.
```sh
go version
```
### JQ (JSON query language Installation
Optional: Install the latest version of jq (only required for the tutorials related to channel configuration transactions).
```sh
sudo apt-get install jq
```

### Step 3: Install Hyperledger Fabric Binaries, Docker Containers & Samples
- Create new directory where you will install Hyperledger Fabric
```sh
mkdir fabric-network
```

### Install Hyperledger Fabric
- To get the install script:
```sh
curl -sSLO https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh && chmod +x install-fabric.sh
```
- To pull the Docker containers and clone the samples repo, run one of these commands for example
```sh
./install-fabric.sh docker samples binary
```
or
```sh
./install-fabric.sh d s b
```

Congrats, you have installed Hyperledger Fabric with all dependencies.

### Step 4: Test the Installation
- To test the our installation, we will run test network that comes with fabric-samples

```sh
cd fabric-samples/test-network
```
```sh
./network.sh down 
```
```sh
./network.sh up 
```

- Using following Docker command we can check all running containers
```sh
docker ps -a
```
**You should be able to see the containers up and running.**

Thank you!