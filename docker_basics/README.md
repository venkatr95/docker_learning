# Install Docker

#### Docker on Windows

Download the Docker desktop from following hyperlink below

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows/) 

* Double-click Docker Desktop Installer.exe to run the installer and follow the installation till finish

* Start Docker desktop

* Verify the installation by following command on CMD

```sh
docker --version
```

* Pull the hello-world image from Docker Hub and run a container

```sh
docker run hello-world
```



#### Docker on Ubuntu
 -  To install Docker CE, first, you need to remove older versions of Docker

```sh
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

- Set up the Docker repository to install and update Docker from the repository using following commands.

```sh
$ sudo apt-get update
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

- Update the apt package index and install the latest version of Docker CE using following commands
```sh
$ sudo apt-get update
```

- Install docker as follows

```sh
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

- After successful installation of the Docker CE package, check status

```sh
$ sudo systemctl status docker
```
It must show Active: active (running)

- Verify that Docker CE is installed properly by running the hello-world image

```sh
$ sudo docker run hello-world
```
Hello from Docker!
This message shows that your installation appears to be working correctly


For more examples and ideas, visit:
 https://docs.docker.com/get-started/