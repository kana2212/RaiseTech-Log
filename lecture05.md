# 第5回課題  

第4回課題で作成したEC2、RDS、VPC、サブネット、AZをそのまま使用し、第3回のCloud9でデプロイしたサンプルアプリをEC2でデプロイする。
起動確認が取れたらALBとS3を追加し、構成図を書いてみる。

## Pumaのみで動作確認  

Ruby,Node,yarn,bundler,mysql,Gitをインストールし、database.ymlファイルにRDSのエンドポイントを指定して先ずはPumaのみで動作確認する。
セキュリティグループのインバウンドルールはポート3000を開放する。

![pumaのみ](pict05/pumaのみ.png)  

## Nginxを追加して動作確認する。  

![Nginxのみ](pict05/Nginxのみ.png)  

## Unicornのみで動作確認  

セキュリティグループのポート3001をテスト用に開放し、unicorn.rbファイルに
```listen 3001```を記述し動作確認する。  

![Unicorn+puma3001確認](pict05/Unicorn+puma3001確認.png)  

## Unicorn+Nginxを連携して動作確認  

UnicornとNginxのソケットのパスが合っていないとエラーが起こる。

![Unicorn+Nginx動作確認](pict05/Unicorn+Nginx動作確認.png)  

## ALB追加  

DNS名を取得できるのでこれを使用してブラウザで接続確認をする。  

![ALB](pict05/ALB.png)  

![ターゲットグループ](pict05/ターゲットグループ.png)  

![ALBのDNS動作確認](pict05/ALBのDNS動作確認.png)  

## I AMロールを設定しS3へ接続する  

ポリシーは「S3FullAccess」をアタッチしてアクセスキー。シークレットキーの代わりとし、EC2インスタンスに割り当てる。
EC2からS3へ接続確認する。

![S3接続確認](pict05/S3接続確認.png)  

## 画像保存に成功  

S3のバケットを作成し、ブラウザから画像を登録して無事に反映されるか確認する。

![画像保存成功](pict05/画像保存成功.png)  

![画像保存時S3](pict05/画像保存時S3.png)  

## 構成図作成  

![Lecture5-ページ2.drawio](pict05/Lecture5-ページ2.drawio.png)  

## 今回の学び  


S3はキャッシュが出ない為、Puma,Nginx,Unicornと起動を分けてそれぞれのエラーログを見る事が大事。
初めに権限も付与する事で余計なエラーに遭遇しなくなった。
今回はシークレットキー、アクセスキーを使用しない方法で実行したのでこの辺りの事も学んでおきたい。
