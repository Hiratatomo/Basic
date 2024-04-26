# Portfolio 構築手順

今後、仕事をする中で必要になってくる、portfolio の作成方法の構築方法を以下に記載する。

- **[Dockerfile を使用した、Web Page を構築手順](#USINGDOCKERFILE)**
- **[Procedure for Building a Web Page Using Dockerfile](#USINGDOCKERFILE-ENGLISH)**  
- **[MOUNT使用した、Web Page を構築手順](#USINGMOUNT)**

## 0. 前提条件  
- ネットワーク通信を行う環境は既に用意されている前提で、リモート（インスタンス）にログイン状態  
- [Docker](https://docs.docker.com/) は remote 環境にインストール済み  

## 1. 環境構築  
1. [Github](https://github.com/Hiratatomo/Basic.git) を開き、「Code」をクリックして、指定されたURLをコピーする  
![code](https://github.com/Hiratatomo/Basic/blob/main/images/code.png)

2. Terminal を開き、クローンしたいディレクトリの場所に現在の作業ディレクトリに移動する  
3. ターミナルに ```git clone``` と入力し、1. で コピーしたURLを貼り付けて、「enter」を押してクローンを作成する  
```git clone https://github.com/Hiratatomo/Basic.git```
4. clone したレポジトリ配下に移動する  
```cd Basic```

<a id="DOCKERFILE"></a>

## **Dockerfile を使用した、Web Page を構築手順**
1. [Dockerfile の作成](#anchor1-1)
2. [Docker イメージをビルドする](#anchor1-2)
3. [Docker イメージをコンテナとして起動する](#anchor1-3)
4. [nginxサーパーでWebページを確認する](#anchor1-4)  

<a id="anchor1-1"></a>

### **Step 1: Dockerfile の作成**  
ディレクトリを作成後、次のそのディレクトリ内に vim エディタを使用して Dockerfile を作成します:  
```$ vim Dockerfile```  
前述のコマンドを実行すると、vim エディタが開きます。次のコンテンツをDockerfileに貼り付けます:  
```
$ FROM nginx:latest
$ COPY . /usr/share/nginx/html
```

<a id="anchor1-2"></a>  

### **Step 2: Docker イメージをビルドする**  

```docker build```コマンドを使用して、Dockerfile をビルドします。作成されるイメージには```latest```というタグをつけ、 イメージにはカスタム名（nginx）を付けます。   

```$ docker build -t nginx:latest .```

イメージがビルドされたら、```docker images``` コマンドを使用してイメージの確認します。 

```docker images``` コマンドは、ビルドされたイメージから pull された全てのイメージのリストを提供します。

```
$ docker images
$ REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
$ nginx        latest    ed998ee43d09   8 minutes ago   193MB
```
<a id="anchor1-3"></a>  

### **Step 3: Docker イメージをコンテナとして起動する**

1. コンテナをデタッチモードで実行し、バックグラウンドで継続的に実行されるようにします。```docker run```  コマンドに ```-d ``` を含めます。
2. また、```--name NAME```で、コンテナ名をつけます。コンテナ実行をコンテナが削除されるように、```--rm```をつけます。また、```-it```を記載し、-i でターミナルからの入力をコンテナが受け付けて、-t でコンテナの標準出力をホストのターミナルに繋げることで、ホストターミナルからコンテナ内部の操作ができるようにします。
3. nginx serverをホストするために、同じポート80（HTTP）を使用します。ウェブサーバーでサーバーを実行するには、-p xxxxx:port を使用します。  


```
$ docker run -it --rm -d -p global address:port --name hirata nginx
```

<a id="anchor1-4"></a>

### **Step 4: Web Pageの状態を確認する**  

Web Page の確認するために、任意のウェブブラウザを開き、次のように入力してください:  
```global address:port```  

上記を入力すると、Portfolio （Web Page）がが表示されます。


<a id="USINGDOCKERFILE-ENGLISH"></a>  

# Building a Web Server through a Dockerfile  
1. [Create a directory](#directory)
2. [Building a Dockerfile](#dockerfile)
3. [Build the Docker image](#dockerimage)
4. [Run the Docker image as a container](#run)
5. [Review the online presence of nginx Server](#review)


<a id="directory"></a>

### **Step 1: Create a directory**  
At first, we make use of [mkdir command](https://www.digitalocean.com/community/tutorials/mkdir-command-linux-unix) to create a directory.  


<a id="dockerfile"></a>

### **Step 2: Building a Dockerfile**  
Having created a folder, now we go ahead and create a Dockerfile within that folder with the vi editor:  
```$ vim Dockerfile```  
As soon as we execute the previous command, a vi editor opens. Paste the following content in the Dockerfile:  
```
$ FROM nginx:latest
$ COPY . /usr/share/nginx/html
```

<a id="dockerimage"></a>  

### **Step 3: Tag and Build the Docker image**  

Now, we build the Dockerfile using the docker build command. Within which, we tag the image to be created as 1.0 and give a customized name to our image (i.e., nginx).  

```$ docker build -t nginx:latest```

Once the image has been built, we should check for the presence of the image using docker images command.  

The docker images command gives us a list of all the images that are built or pulled from any public/private registry.

```
$ docker images
$ REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
$ nginx        latest    ed998ee43d09   8 minutes ago   193MB
```

<a id="run"></a>  

### **Step 4: Run the Docker image as a container**

1. We run the container in detached mode so that it runs continuously in the background. Include -d in the docker run command.  
2. In order to host the Apache server, we provide port 80 (HTTP) for the same. Make use of -p 20091:80 to have the server running on web server.  

```
$ docker run -it --rm -d -p 20091:80 --name hirata nginx
```

<a id="review"></a>

### **Step 5: Review the online presence of nginx Server**  
システム上のWebサーバーの存在をテストするために、任意のウェブブラウザを開き、```52.194.188.6:80```を入力してください。  
上記のURLを開くと、Web Pageが表示されます。

<a id="USINGMOUNT"></a>  

## Web Page を構築手順
1. [nginx image を pull する](#anchor2-1)
2. [Bind Mountを使用し、nginx を起動する](#anchor2-2)
3. [nginxサーパーでWebページを確認する](#anchor2-3)

<a id="anchor2-1"></a>  

### **Step 3: nginx image を pull する**  
```docker pull nginx```

<a id="anchor2-2"></a>  

### **Step 3: Bind Mountを使用し、nginx を起動する**  
```docker run --name containername -p 00000:80 -v /path/to/index.html:/usr/share/nginx/html:ro -d nginx```  
このコマンドは、nginx ベースの Docker コンテナ内で default bin/bash セッションを開始し、現在のディレクトリをコンテナ内の "/app" ディレクトリにバインドマウントする。バッググラウンドで動作させるために ```-d```をつける。

<a id="anchor2-3"></a>  

### **Step 3: Webページを確認する

Web Page の確認するために、任意のウェブブラウザを開き、次のように入力してください:  
```52.194.188.6:80```  

上記を入力すると、Portfolio （Web Page）がが表示されます。


<a id="reference"></a>

### References  
[Building an Apache Web Server through a Dockerfile](https://www.digitalocean.com/community/tutorials/apache-web-server-dockerfile)
[How to clone a git repository using the command line](https://www.educative.io/answers/how-to-clone-a-git-repository-using-the-command-line)
