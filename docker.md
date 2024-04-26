# Docker

> Docker is an platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly.  
With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker's methodologies for shipping, testing, and deploying code, you can significantly reduce the delay between writing code and running it in production.  
[Docker overview](https://docs.docker.com/get-started/overview/)

1. [Advantages of utilizing Docker](#advantages)
2. [Ways to use Docker](#usecases)
3. [Basic Operations](#operation)
4. [Reference](#reference)
5. [learning](#learning)



<a id="advantages"></a>

### **1. Advantages of utilizing Docker**

Docker provides a range of benefits for developers and operations teams, including increased efficiency, flexibility, portability, and security. By using Docker, organizations can streamline their development and deployment processes, reduce costs, and improve overall efficiency.  
[https://www.linkedin.com/pulse/what-docker-benefits-using-anand-mohan#:~:text=In%20conclusion%2C%20Docker%20provides%20a,costs%2C%20and%20improve%20overall%20efficiency.](https://www.linkedin.com/pulse/what-docker-benefits-using-anand-mohan#:~:text=In%20conclusion%2C%20Docker%20provides%20a,costs%2C%20and%20improve%20overall%20efficiency.)

<a id="usecases"></a>

### **2. Use cases of Docker**

> - **Microservices**  
Due to docker, the applications can be broken down into smaller, manageable components. The deployment and development of microservices-based architecture are facilitated by docker.  
> - **Containers**  
The management and creation of isolated, lightweight containers are enabled by docker. These containers encapsulate the dependencies of an application and make sure that it is consistent across multiple environments.  
> - DevOps Adoption  
The software delivery process gets streamlined by docker as it helps organizations embracing DevOps principles. It is done by enabling collaboration between the operations and development teams.  
> - **Software Testing**  
The developer is allowed by docker to test their applications in reproducible, isolated containers. The process of managing and setting up testing environments is simplified by docker.  
> - **Continuous Deployment**  
One can achieve continuous delivery and integration easily due to docker. This is because the automated and rapid deployment of applications is enabled by docker.  
> - **Legacy App Migration**  
The migration of legacy applications to containerized environments is facilitated by docker. This improves the scalability, portability, and ease of management of legacy applications.
>> - What are Microservices?  
In software development, microservices are an architectural approach. In this approach, applications are built as a collection of independent, small, and loosely coupled services. Specific functionality is represented by each service. Each can be deployed and developed independently. Well-defined APIs are used to communicate with other services. 
>> - What are Containers?  
Isolated, lightweight environments in which an application and its dependencies are encapsulated in known containers. They allow applications to run consistently and reliably across multiple computing environments providing a portable and consistent runtime environment. 
> [https://www.simplilearn.com/docker-use-cases-article](https://www.simplilearn.com/docker-use-cases-article)


<a id="operation"></a>

### **3. Executing fundamental container tasks on a Mac.**  

  3-1. Download an image from a registry  
  To download a particular image, or set of images (i.e, a repository) use ```docker image pull``` (or the ```docker pull``` shorthand). If no tag is provided, Docker Engine uses the ```:latest``` tag as a default. This example pulls the ```ubuntu:latest``` image:    

  - ```docker pull ubuntu (docker image pull ubuntu)```  

  ```
  Using default tag: latest
  latest: Pulling from library/ubuntu
  3c645031de29: Pull complete
  Digest: sha256:1b8d8ff4777f36f19bfe73ee4df61e3a0b789caeff29caa019539ec7c9a57f95
  Status: Downloaded newer image for ubuntu:latest
  docker.io/library/ubuntu:latest
  ```  
  
3-2. To see which images are present locally, use ```docker images``` commands:  
```
$ docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
ubuntu       latest    7af9ba4f0a47   2 weeks ago   77.9MB
```

3-3. Running containers  

```$ docker run -it --name "ubuntu" ubuntu``` 


**General form**  

A **docker run** commands takes the following form:

```$ docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]```

**Image references**  
The image reference is the name and version of the image. You can use the image reference to create or run a container based on an image.  
- ```docker run IMAGE[:TAG][@DIGEST]```
- ```docker create IMAGE[:TAG][@DIGEST]```  
An image tag is the image version, which defaults to ```latest``` when omitted. Use the tag to run a container from specific version of an image. For example, to run version ```23.10``` of the ```ubuntu``` image: ```docker run ubuntu:23.10```.

**Options**

```[OPTIONS]```  
let you configure options for the container. For example, you can give the container a name (--name), or run it as a background process (-d). You can also set options to control things like resource constrains and networking.  

**Commands and arguments**  

You can use the ```[COMMAND]``` and ```[ARG...]``` positional arguments to specify commands and arguments for the container to run when it starts up. For example, you can specify ```sh``` as the ```[COMMAND]```, combined with the ```-i``` and ```-t``` flags, to start an interactive shell in the container (if the image you select has an ```sh``` executable on ```PATH```).  
```$ docker run -it IMAGE sh```  

**Foreground and background**  

When you start a container, the container runs in the foreground by default. If you want to run the container in the background instead, you can use the **--detach** (or **-d**) flag. This starts the container without occupying your terminal window.

```$ docker run -d IMAGE```

[https://docs.docker.com/engine/reference/run/](https://docs.docker.com/engine/reference/run/)


3-4. List Containers  
  
Show both running and stopped containers (-a, --all)
The ```docker ps``` command only shows running containers by default. To see all containers, use the --all (or -a) flag:  
```$ docker ps -a```  
```output
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
5df93e7afc17   ubuntu    "/bin/bash"   12 minutes ago   Up 12 minutes             ubuntu
```

3-5-1. check the directory  
```$ ls```  
```
bin   dev  home  lib32  libx32  mnt  proc  run   srv  test.txt  usr
boot  etc  lib   lib64  media   opt  root  sbin  sys  tmp       var
``` 

When the ls command can't use, you can use next command.  
```$ docker exec -it <container> bash```  
```$ docker run -it <image> bash```
[Run Bash Shell In Docker](https://www.warp.dev/terminus/docker-run-bash)


3-5-2. edit a file using vim.  
```
// make a file
$ touch sample.txt
// edit a file
$ vim sample.txt
```

When you can's use the vim command, you can install next commands.  
```
$ apt-get update
$ apt-get install vim 
```


4. Stop one or more running containers  

**Usage** ```docker container stop [OPTIONS] CONTAINER [CONTAINER...]```  
```$ docker stop my_container```  
[docker container stop](https://docs.docker.com/reference/cli/docker/container/stop/)

5. Restart one or more containers  
**Usage** ```Usage	docker container restart [OPTIONS] CONTAINER [CONTAINER...]```  
```$ docker restart my_container```  
[docker container restart](https://docs.docker.com/reference/cli/docker/container/restart/)


6.  To remove (delete) all locally installed Docker images from my machine.
```
$ docker rmi $(docker images -a -q)
```  
[Remove All Docker Images](https://www.warp.dev/terminus/docker-remove-all-images#:~:text=The%20docker%20rmi%20command%20is,Docker%20images%20including%20dangling%20ones.)


<a id="reference"></a>

### Reference
- [docker.docks](https://docs.docker.com/)  


<a id="learning"></a>  

### **Learning**  
- Image digests  
> Images using the v2 or later image format have a content-addressable identifier called a digest. As long as the input used to generate the image is unchanged, the digest value is predictable.  

The following example runs a container from the ```alpine``` image with the ```sha256:9cacb71397b640eca97488cf08582ae4e4068513101088e9f96c9814bfda95e0``` digest:  
```$ docker run alpine@sha256:9cacb71397b640eca97488cf08582ae4e4068513101088e9f96c9814bfda95e0 date```


- centOS 仮想環境構築
```docker pull centos:latest```
CentOS の Packages の Download の参照先が古い場合は、更新が必要。  
```
cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
```  
```yum install vim```
