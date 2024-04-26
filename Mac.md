# Mac Environment Setup

1. [Homebrew](#anchor1)
2. [Git](#anchor2)
3. [Github Desktop](#anchor3)
4. [Github Account](#anchor4)
5. [Docker Desktop](#anchor5)
6. [Docker](#anchor6)
7. [Docker-Compose](#anchor7)
8. [Visual Studio Code](#anchor8)

<a id="anchor1"></a>

### **1. Homebrew**

> HomebrewとはmacOS上で動作するパッケージ管理ツールで、このHomebrewを用いて様々なパッケージをインストールすることができます。
[https://zenn.dev/sawao/articles/e7e90d43f2c7f9](https://zenn.dev/sawao/articles/e7e90d43f2c7f9)

macOSのターミナルまたはLinuxのシェルスクリプトのプロンプトに貼り付ける。

```/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"```

```brew -v```

- [Homebrew macOS（またはLinux）用パッケージマネージャー](https://brew.sh/ja/)

<a id="anchor2"></a>

### **2. Git**

> Git とはソースコードや変更履歴を管理するために使われる、代表的な分散型パージョン管理システム。  
[https://www.kagoya.jp/howto/it-glossary/develop/git/](https://www.kagoya.jp/howto/it-glossary/develop/git/)   
[What is Git?](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)

There are several options for installing Git on macOS. Note that any non-source distributions are provided by third parties, and may not be up to date with the latest source release.

**Homebrew**  
```brew install git```

**MacPorts**  
```sudo port install git```

```$ git -v```

[Download for macOS](https://git-scm.com/download/mac)


<a id="anchor3"></a>

### **3. Github Desktop**

> Github とは、Gitの仕組みを利用したウェブ上のバージョン管理サービス。
[https://www.kagoya.jp/howto/it-glossary/develop/git/](https://www.kagoya.jp/howto/it-glossary/develop/git/)


1. Visit the (download page for Github Desktop)[https://desktop.github.com/]  
2. Click **Download for macOS**  
3. In your computer's ```Downloads``` folder, double-click the **GitHub Desktop** zip file.  
4. After the file has been unzipped, double-click the **GitHub Desktop** application file.  
5. GitHub Desktop will launch after installation is complete.

- [Installing GitHub Desktop](https://docs.github.com/en/desktop/installing-and-authenticating-to-github-desktop/installing-github-desktop)

<a id="anchor4"></a>

### 4. Create Github Account (Company Address)

1. Navigate to https://github.com/.  
2. Click **Sign up**.
3. Follow the prompts to create your personal account.

(Creating an account on GitHub)[https://github.com/join]

<a id="anchor5"></a>

### 5. Docker Desktop

> Docker Desktop とは、Windows・MacOs上でDocker環境を構築・利用するためのツール。Docker Desktop では、専用の管理画面上でコンテナの停止や再開、廃止といった作業が可能。

Please proceed from the following link.

[Install Docker Desktop for Mac](https://docs.docker.com/desktop/install/mac-install/)

<a id="anchor6"></a>

### 6. Docker

> Dockerは、インフラ関係やDevOps界隈で注目されている技術の一つで、Docker社が開発している、コンテナ型の仮想環境を作成、配布、実行するためのプラットフォームです。  
[https://www.docker.com/what-docker](https://www.docker.com/what-docker)

```$ docker ps```
```$ docker --version```

[Docker for Mac を始めよう](https://docs.docker.jp/docker-for-mac/index.html)

<a id="anchor7"></a>

### 7. Docker Compose

> Docker Compose とは、複数コンテナのアプリケーションを定義・共有するために役立つように、開発されたツールです。  
[https://docs.docker.jp/get-started/08_using_compose.html#:~:text=Docker%20Compose%20%E3%81%A8%E3%81%AF%E3%80%81%E8%A4%87%E6%95%B0,%E5%89%8A%E9%99%A4%E3%81%97%E3%81%9F%E3%82%8A%E3%81%A7%E3%81%8D%E3%81%BE%E3%81%99%E3%80%82](https://docs.docker.jp/get-started/08_using_compose.html#:~:text=Docker%20Compose%20%E3%81%A8%E3%81%AF%E3%80%81%E8%A4%87%E6%95%B0,%E5%89%8A%E9%99%A4%E3%81%97%E3%81%9F%E3%82%8A%E3%81%A7%E3%81%8D%E3%81%BE%E3%81%99%E3%80%82)

```$ docker-compose --version```

[Docker Compose のインストール](https://docs.docker.jp/v1.10/compose/install.html)

<a id="anchor8"></a>

### 8. Visual Studio Code

> Visual Studio Code は、マイクロソフトが開発したオープンソースのコードエディタで、軽量かつ高速、高機能が特徴です。多くのプログラミング言語に対応し、 Git との統合やデバッグ機能なども備えています。また、クロスプラットフォーム対応であり、 Windows 、 Mac 、 Linux で使用できるのが魅力です。  
[https://www.rworks.jp/cloud/azure/azure-column/azure-entry/28456/](https://www.rworks.jp/cloud/azure/azure-column/azure-entry/28456/)

- spotlight 検索

[Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac)