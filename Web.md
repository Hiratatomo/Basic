# Web 

0. [用語解説](#anchor1)


<a id="anchor1"></a>

0. 用語説明

- Nginx

> Nginxは、高性能かつ軽量なWeb serverで、特に大規模な Web application や 高トラフィック環境での使用に適している。  
その特徴の一つが、**イベント駆動型アーキテクチャ"" である。  
  - Nginx の強み

  > Nginxのイベント駆動型及びノンブロッキングI/O アーキテクチャが、特に同時大量アクセスの処理において優れている。

    - イベント駆動型

    > イベント駆動型アーキテクチャーとは、イベントの公開、取得、処理、保存（または持続）を中心に構築された、統合モデルです。 具体的には、アプリケーションやサービスが、別のアプリケーションやサービスが知りたいと考えるようなアクションを実行する際、または変化する際に、イベント（そのようなアクションや変化の記録）を公開します。

    (イベント駆動型アーキテクチャーとは)[https://www.ibm.com/jp-ja/topics/event-driven-architecture#:~:text=%E3%82%A4%E3%83%99%E3%83%B3%E3%83%88%E9%A7%86%E5%8B%95%E5%9E%8B%E3%82%A2%E3%83%BC%E3%82%AD%E3%83%86%E3%82%AF%E3%83%81%E3%83%A3%E3%83%BC%E3%81%A8%E3%81%AF%E3%80%81%E3%82%A4%E3%83%99%E3%83%B3%E3%83%88%E3%81%AE%E5%85%AC%E9%96%8B,%E8%A8%98%E9%8C%B2%EF%BC%89%E3%82%92%E5%85%AC%E9%96%8B%E3%81%97%E3%81%BE%E3%81%99%E3%80%82]

    - I/O アーキテクチャ

    > ノンブロッキングI/OはI/O処理を非同期に行う方法で、プログラムがI/O処理が完了するのを待たずに他の処理を行うことができます。 ノンブロッキングI/Oを使用すると、I/O処理が完了するのを待たずに、プログラムはその間に他の処理を行うことができます

    (ノンブロッキングI/Oとは何か？初心者向けの説明)[https://note.com/nasuyasu66/n/ne47ff6830ba5]



### 1. Web page が browser に表示される仕組み

> Webページは主に3つのプログラム（HTML、CSS、JavaScript）によって表現されます。  
それらのプログラムはブラウザからURLにアクセスした結果、最終的にWebサーバーから転送されます。  
転送されたプログラムをブラウザが解析・処理を行い、私たちが普段見ているようなWebページが表示されます。  

[Webページが表示される仕組み](https://qiita.com/sugurutakahashi12345/items/3cc26f23b82f344fa188#:~:text=7.%20%E3%81%BE%E3%81%A8%E3%82%81-,Web%E3%83%9A%E3%83%BC%E3%82%B8%E3%81%AF%E4%B8%BB%E3%81%AB3%E3%81%A4%E3%81%AE%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%A0%EF%BC%88HTML%E3%80%81CSS,JavaScript%EF%BC%89%E3%81%AB%E3%82%88%E3%81%A3%E3%81%A6%E8%A1%A8%E7%8F%BE%E3%81%95%E3%82%8C%E3%81%BE%E3%81%99%E3%80%82&text=%E3%81%9D%E3%82%8C%E3%82%89%E3%81%AE%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%A0%E3%81%AF%E3%83%96%E3%83%A9%E3%82%A6%E3%82%B6,%E3%83%9A%E3%83%BC%E3%82%B8%E3%81%8C%E8%A1%A8%E7%A4%BA%E3%81%95%E3%82%8C%E3%81%BE%E3%81%99%E3%80%82)


### 2. mac 上で簡単に HTML file を書いて、browser で開いてみる。

### 3. mac に nginx を導入して起動し、browser からアクセスして、HTML を表示

1. homebrew でinstall  
``` $ brew install nginx ```  
2. nginx が入っているか確認  
``` $ nginx -v ```  
3. nginx を起動する   
``` $ brew services start nginx ```  
4. どのポートが開いているのかを lsof 確認  
``` $ lsof -c nginx -P | grep LISTEN ```   
```
nginx   9685 brainsadmin2024    6u    IPv4 0x54cbc3267d212f7b      0t0     TCP *:8080 (LISTEN)
nginx   9688 brainsadmin2024    6u    IPv4 0x54cbc3267d212f7b      0t0     TCP *:8080 (LISTEN)
```
- nginx の設定ファイルの場所  
``` $ brew info nginx ```  
> The default port has been set in ```/usr/local/etc/nginx/nginx.conf``` to 8080 so that
nginx can run without sudo.  
```/usr/local/var/www/index.html```

### 4. mac 上の Docker で nginx container を起動し、browser からアクセスしてHTML を表示

1. Docker上でnginx を動かす手順  
    1-1.   nginx の Image を取得する  
    ```docker image pull nginx```  
    1-2.   nginx を動作させる  
    ```docker container run -d -p 8080:80 --name nginx nginx```    
    1-3.  作成した container をコマンドで停止・起動  
      - 停止 ```docker container stop nginx```  
      - 起動 ```docker container start nginx```

    1-4. nginx で自分の作ったhtml file を表示する。  
      - 1-4-1  nginx コンテナの中へ入る  
      ```docker container exec -it nginx bash```
      - 1-4-2 以下のコマンドでnginx 設定fileの内容を確認する  
      ```cat /etc/nginx/conf.d/default.conf```  
      ```  
      location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
      }
      ```

      - Install vim  
      ```
      apt-get update
      apt-get install vim
      ```  
      - vim コマンドで file を編集する  
      ```vim /usr/share/nginx/html/index.html```


### References

[【入門】Dockerでnginxを動かす手順](https://www.kagoya.jp/howto/cloud/container/dockernginx/)