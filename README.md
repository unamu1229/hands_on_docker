# ubuntuコンテナへの接続方法
docker exec -it hands_on_ubuntu script -q -c "/bin/bash"

# ubuntuコンテナからDB接続コマンド
mysql -u root -psecret2q3 -h 172.16.1.1

# ローカルファイルとubuntuコンテナ間のファイル共有
docker-compose.ymlのservices>ubuntu>volumesの〇〇〇:/opt/hands_onの
〇〇〇の箇所にローカルファイルの場所を設定する

# 始め方
docker-compose up -d

cd /opt/hands_on/