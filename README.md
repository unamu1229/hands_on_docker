# hands_on_ubuntuコンテナへの接続方法
docker exec -it hands_on_ubuntu script -q -c "/bin/bash"

# hands_on_ubuntuコンテナからDB接続コマンド
mysql -u root -psecret2q3 -h 172.16.1.1

# ローカルファイルとhands_on_ubuntuコンテナ間のファイル共有
docker-compose.yml の services > hands_on_ubuntu > volumes の 〇〇〇:/opt/hands_on 
の〇〇〇の箇所にローカルファイルの場所を設定する

# 始め方
docker-compose up -d

# hands_on_ubuntuコンテナでphpstormからphpunitを動かす為の設定
※docker-composeの設定だと、phpstormのユニットテストで生成された  
コンテナ名と、docker-compose up -dで作成されたコンテナ名が重複して生成できない。  
同じdocker-compose.ymlを利用しているのに、双方が別のdocker-composeとみなされていそう。  
なので、hands_on_ubuntuコンテナに普通にssh接続して、コンテナのphpunitを利用する方法にする。  

CLI Interpretersを設定する
Passwordは screencast

Languages & Frameworks > PHP の　Path mappings も設定する  

他の設定も必要かもしれないけど、とりあえずphpstormからphpunitを実行して、設定漏れの警告がでたら設定してあげる
