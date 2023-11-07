# RaiseTech AWSコース課題用リポジトリ
このリポジトリはRaiseTechのAWSフルコース用課題に取り組んできたまとめになります。

## 取り組み内容


以下は各課題の詳細となります。

| 　                 ファイル        　                                               | 課題内容                                                                                                                                                                                                               |
|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [lecture02](https://github.com/kana2212/RaiseTech-Log/blob/main/lecture02.md) | Gitの概要とターミナルの連携                                                                                                                                                                                                    |
| [lecture03](https://github.com/kana2212/RaiseTech-Log/blob/main/lecture03.md) | Ruby on Railsで作成された[サンプルアプリケーション](https://github.com/yuta-ushijima/raisetech-live8-sample-app)をCloud9上でデプロイする                                                                                                      |
| [lecture04](https://github.com/kana2212/RaiseTech-Log/blob/main/lecture04.md) | VPC,EC2,RDSを構築。その後EC2からRDSへ接続し、正常に接続できるよう設定する                                                                                                                                                                      |
| [lecture05](https://github.com/kana2212/RaiseTech-Log/blob/main/lecture05.md) | lecture04で構築した環境を下地にEC2上で[サンプルアプリケーション](https://github.com/yuta-ushijima/raisetech-live8-sample-app)のデプロイを実施する  組み込みサーバー(Puma)起動確認後、Webサーバー(Nginx),APサーバー(Unicorn)に分けて起動。正常動作確認後にALBを追加。 アプリケーション内で使用する画像保存先をS3に変更 |
| [lecture06](https://github.com/kana2212/RaiseTech-Log/blob/main/lecture06.md)                                                                 | CloudTrailとCloudWatchの概要について学習し、異常発生時にメールに通知が来るように設定。                                                                                                                                                              |
| [lecture07](https://github.com/kana2212/RaiseTech-Log/blob/main/lecture07.md)                                                                 | 現在の構成で考えられる負荷対策や脆弱性についての考察                                                                                                                                                                                         |                                                                                                                                                                                                                   |

## 成果物  
### 手動構築とRailsアプリのデプロイ  
AWSの環境構築とRailsアプリの構成は下記の図となっています。  
EC2のOSはAmazonlinux2を利用。  
RDSはMySQLでDBを作成、Private Subnetに配置しEC2のみ通信可能になるようにSecurity Groupを設定。
RailsアプリのWEBサーバーとAPサーバーは組み込みのPumaでのデプロイとNginxとUnicornを組み合わせたデプロイの両方を実施しています。  
S3に画像を保存するよう設定しています。

![Lecture5-ページ2.drawio](pict05/Lecture5-ページ2.drawio.png)  
