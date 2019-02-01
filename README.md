# ハンズオンの始め方
## hands_on_DDDリポジトリファイルとhands_on_ubuntuコンテナ間のファイル共有　　
docker-compose.yml の services > hands_on_ubuntu > volumes の 〇〇〇:/opt/hands_on_DDD
の〇〇〇の箇所にhands_on_DDDリポジトリをpullした場所を設定する。　　
## コンテナに入ってphpunitやautoloadのファイルをインストール
```
docker-compose up -d
docker exec -it hands_on_ubuntu script -q -c "/bin/bash"
cd /opt/hands_on/
composer install
```
これで下記コマンドでテストを実行できます。
```
vendor/bin/phpunit tests
```

下記以降はphpstormでphpunitを実行したい方向け　　


# hands_on_ubuntuコンテナでphpstormからphpunitを動かす為の設定
※docker-composeの設定だと、phpstormのユニットテストで生成された  
コンテナ名と、docker-compose up -dで作成されたコンテナ名が重複して生成できない。  
同じdocker-compose.ymlを利用しているのに、双方が別のdocker-composeとみなされていそう。  
なので、hands_on_ubuntuコンテナに普通にssh接続して、コンテナのphpunitを利用する方法にする。  

## CLI Interpretersを設定する  
![CLI Interpreters](https://bitbucket.org/h_yoneda/hands_on_docker/raw/93a9c9357c08fd29baac2b9a7510fe9b1c93cd06/CLI_Interpreters.png)  
Passwordは screencast
## Test Frameworksを設定する
![Test Frameworks](https://bitbucket.org/h_yoneda/hands_on_docker/raw/19baa615e84d47f97a641f235c586771ff78d48f/TestFrameworks.png)
## Languages & Frameworks > PHP の　Path mappings を設定する  
※Path to scriptの設定時にssh接続エラーが出る時、ToolsのStart SSH Sessionを試してみる


他の設定も必要かもしれないけど、とりあえずphpstormからphpunitを実行して、設定漏れの警告がでたら設定してあげる

# hands_on_ubuntuコンテナへの接続方法
docker exec -it hands_on_ubuntu script -q -c "/bin/bash"

# hands_on_ubuntuコンテナからDB接続コマンド
mysql -u root -psecret2q3 -h 172.16.1.1

# hands_on_ubuntuコンテナへのsshコマンド接続方法
ssh root@127.0.0.1
パスワード : screencast