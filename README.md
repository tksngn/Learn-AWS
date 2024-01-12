# AWSを学ぼう
## 9章 【AWSサービス構成実践-2】-9章からpush開始
 - 「サーバーレス」とは
### AWSのサーバーレスサービス
 - 「AWS Lambda」とは
## 10章【AWSサービス構成実践-3】
 - 学習の目標
 - 画像をアップロードする機能を実装する
 - 構成イメージ
 - AWSの環境を設定する
 - Railsアプリケーションを実装する(refileを使用する場合)
 - Railsアプリケーションを実装する(ActiveStorageを使用する場合)
 - まとめ
## 【補足コンテンツ-I】-用語説明
### IT用語
 - TCP/IP…プロトコル群（通信規約）の相称
 - Cookie…ブラウザで保持されるテキストデータ
 - Session…Webサーバーで保持されるデータ
 - ロードバランサー…アクセスを複数のサーバーに分割して処理
 - ドメイン…IPアドレスをわかりやすい名前に変換したもの
 - キーペア…公開鍵・秘密鍵のペアのこと
 - JSON…JavaScript Object Notationの略で、テキストベースのデータ交換フォーマット
 - API(Application Programming Interface)…サービス提供者がそのサービスを利用するためのインターフェース
 - Web API…WebサーバーやWebブラウザ用のAPI
 - DR(ディザスタリカバリ)…自然災害やサイバー攻撃などでデータセンターやシステムの稼働に問題が発生した場合に損害の軽減や機能の維持、回復や復旧のための対策のことです。代表的な方式としてホットスタンバイやコールドスタンバイなどが存在します。
 - オンプレミス…サーバーやネットワークなどシステムのインフラ環境を、自社保有や他社運営のデータセンター設備を借りて機器を設置し自社にて管理や運営を行う形態。自社運用とも訳される
 - CORS…Cross-Origin Resource Sharingの略で、日本語では「オリジン間リソース共有」と言います。対象のサイトにおいて特定サイトへの通信を許可する仕組みです。
### IPアドレス(Internet Protocol Address)=ネットワーク上に接続された機器が持っている番号
 - パブリックIPアドレス…インターネットからアクセス可能なIPアドレス。インターネット上で必ず一意に割り振られる
 - プライベートIPアドレス…インターネトからアクセスできないIPアドレス
 - CIDR(Classless Inter-Domain Routing)…ネットワーク部やホスト部（IP アドレスの範囲）を決める方法
### 使用プロトコル一覧
 - TCP…コネクション型で信頼性のあるトランスポート層のプロトコル
 - UDP…コネクションレス型で信頼性のないトランスポート層のプロトコル
 - HTTP(Hyper Text Transfer Secure)…HTML,CSS ファイル、メディアファイルなどを送受信するためのプロトコル（ポート番号80）
 - HTTPS(Hypertext Transfer Protocol Secure)…HTTP 通信を TLS/SSL という仕組みで暗号化しHTML,CSS ファイル、メディアファイルなどを送受信をするプロトコル(ポート番号443）
 - SSH(Secure Shell)…暗号化技術を使い、安全に他のコンピュータを遠隔操作するためのプロトコル(ポート番号22）
 - DNS(Domain Name System)…ドメインを IP アドレスに変換するためのプロトコル(ポート番号53）
 - ICMP/ICMPv6（Internet Control Message Protocol)…通信状態の診断を行うためのプロトコル
### 使用ソフトウェア・言語
 - Nginx…オープンソースのWebサーバー
 - Amazon Linux2…AWSが提供するLinux OS（Red Hat7というLinux OSをベースに作成されている）
 - Node.js…ブラウザ上でしか動作することが出来なかったJavaScriptをサーバー上で動かせるようにするための実行環境
## AWS用語説明
### AWS用語
 - リージョン…AWS がサービスを提供しているエリア（国・地域）のこと
 - AZ（アベイラビリティーゾーン）…データセンターのことで、実際にサービスが稼働する場所のこと
## SDK・CLI
 - AWS SDK(Software Development Kit)…AWSが提供する公式ライブラリの1つ
 - AWS CLI(Command Line Interface)…LinuxやWindowsのコマンドラインでAWSのサービスを操作するのに使用
### AWS利用サービス説明
### EC2 (Amazon Elastic Compute Cloud)
 - パブリックIPv4アドレス(グローバルIPアドレス)…インターネットからアクセス可能な IP アドレスです。この IP アドレスはインターネット上で必ず一意に割り振られます
 - プライベートIPv4アドレス…インターネットからアクセスができない IP アドレスです。VPC インスタンス間の通信で利用できます。
 - EIP(Elastic IP)…AWS で固定 IP アドレスを利用するためのサービス
 - AMI(Amazon Machine Image)…EC2 インスタンスの構成を取得し、テンプレートを作成するサービスです。EC2 インスタンスの全内容をバックアップすることができます
 - EBS(Elastic Block Store)…ネットワークを介してEC2インスタンスにアタッチされるボリュームです
 - インスタンスストア…EC2インスタンスに直接アタッチされるボリュームです
 - Amazon EFS…AWSが提供するNFS(Network File System)を使用するファイルストレージ
 - ロードバランサー…・ALB(Application Lord Balancer)・NLB(Network Lord Balancer)・Classic Lord Balancer(旧来のロードバランサーでELBと呼ばれていた）の3種類をサポート
 - ALB(Application Lord Balancer)…アプリケーションへのトラフィックを複数の多^ゲットに分散するサービス
### AWS Lambda(AWS が提供するサーバーの起動や管理なしで、コード（Lambda 関数）を自動実行できるサービス)
 - レイヤー（Lambda レイヤー）…ライブラリを複数の Lambda 関数で共有することができる
### AWS S3(Amazon Simple Storage Service)…AWS が提供するクラウド上にデータやファイルを保存できるサービス
 - バケット…オブジェクトを保持するための場所
 - オブジェクト…バケットに保持されているファイル本体
 - メタデータ…オブジェクトに付属する属性情報
 - バケットポリシー…外套のバケットにアクセスできるユーザーを指定し、JSON形式のポリシードキュメントで、アクセス許可・拒否の条件を細かく制御できる
 - S3 Intelligent-Tiering…データのアクセスパターンに基づき、ストレージクラスを自動的に最適化する機能
 - AWS S3 Glacier…S3 同様クラウド上にデータやファイルを保存できるアーカイブ、バックアップ向けのサービス
### VPC(Virtual Private Cloud)…AWS 上に構築する仮想ネットワークです。 作成時に、作成する VPC の IPv4 のアドレス範囲を指定する必要がある
 - セキュリティグループ…インスタンスの通信を遮断する目的で作られる仮想ファイアウォール
 - インバウンドルール…外部からVPCへのアクセス制御をする
 - アウトバウンドルール…VPCから外部へのアクセス制御をする
 - サブネット…VPCのIPアドレス範囲の中で、さらに小さな仮想ネットワークを作成するもの
 - ルートテーブル…サブネット内の AWS リソース（EC2 インスタンスなど）がどこに通信しにいくのか、そのルールを定めるもの
 - インターネットゲートウェイ…EC2 インスタンスなどの AWS リソースとインターネット間で通信できるようするもの
 - パブリックサブネット…インターネットに接続できるサブネット
 - プライベートサブネット…インターネットに接続できないサブネット
### IAM(Identity and Access Management)…AWS のユーザーと、ユーザーのアクセス権限を管理するサービス
 - ロール…AWS リソースの権限を付与・管理
 - ユーザー…AWS へのアクセス権限を持ったユーザーを作成・管理
 - グループ…同じ権限を持ったユーザーの集まりを作成・管理
 - ポリシー…ユーザーやロールがどのサービスにアクセスできるのかルールを作成・管理
### その他のサービス
#### ネットワーキングとコンテンツ配信サービス
 - Amazon API Gateway…AWS が提供する API の作成、配布、保守、監視、保護が行えるサーバーレスサービス
 - Route53…AWS が提供する DNS(Domain Name Service)サービス
 - Cloud Front…AWS のコンテンツ配信サービス（コンテンツデリバリーネットワーク：CDN）S3 上にある画像や動画、ファイルなどを高速に配信する際に利用
#### データベースサービス
 - RDS(Relational Database Service)…AWS が提供するフルマネージドのリレーショナルデータベースサービスです。Amazon Aurora/PostgresSQL/MySQL/ORACLE などに対応
 - DynamoDB…AWS が提供する NoSQL（Not only SQL）型のデータベースサービス
#### 管理とガバナンスサービス
 - CloudWatch…AWS が提供する、AWS リソースや AWS 上で実行中のアプリケーションをリアルタイムで監視（モニタリング）するマネージドサービス
 - CloudTrail…AWS が提供する、ユーザーや AWS サービス（SDK、API、CLI）などによって実行されたアクションがイベントとして記録されるサービス
 - Trusted Advisor…AWS の利用状況をチェックしコスト最適化・パフォーマンス・セキュリティ・耐障害性（フォールトトレランス）・サービス制限の 5 つの観点から改善した方がいい点を通知するサービス
#### AWSコスト管理サービス
 - AWS Cost Explorer…AWS の各サービスの使用量を時系列でグラフ化するツール
 - AWS Budgets…予算のしきい値を超えたとき（または、超えると予測されたとき）に、アラートを発信できる機能
 - AWS Pricing Calculator…AWS の料金を試算するツール
#### 開発者用ツールサービス
 - Cloud9…AWS が提供するクラウドベースの統合開発環境サービスです。アプリケーションの開発やデータベースなどをクラウド環境で利用することが出来る
#### アプリケーション統合サービス
 - Amazon SNS (Simple Notification Service)…AWS が提供する、メッセージ配信を提供するマネージド型のサービス
#### セキュリティ、ID、およびコンプライアンスサービス
 - ACM (AWS Certificate Manager)…AWS サービスと SSL 証明書の管理を簡単にするツール
## 【補足コンテンツ-II】-IPアドレスを学ぼう
### IPアドレスとは？
#### Macの場合
 - $ ifconfig en0
#### Windowsの場合
 - $ ipconfig
   >ifconfigやipconfigは、ネットワークインターフェースの状況を確認するコマンド
   >10.0.0.0 ～ 10.255.255.255
   >172.16.0.0 ～ 172.31.255.255
   >192.168.0.0 ～ 192.168.255.255
 - パソコンに割り当てられているIPアドレス（住所）です。
### IPアドレスの管理
 - ネットワーク上の住所に当たるIPアドレスは、好きな番号を自由に設定できるわけではありません。IPアドレスは「ICANN」によって全世界的に管理され、世界共通のルールで運用されています。

   ICANNの下には、地域（北米地域、欧州地域、アジア太平洋地域など）ごとにIPアドレスの管理を委任されている組織（インターネットレジストリ）があります。
   各地域のインターネットレジストリが、それぞれの地域内のIPアドレス割り当て業務を行っていて、日本国内のIPアドレスは「JPNIC」（日本ネットワークインフォメーションセンター）が管理しています。
   JPNICは、国内のIPアドレス管理指定業者（データセンター事業者やインターネットプロバイダー）へ、IPアドレスを割り当てています。
#### 割り当ての状況を確認する-nslookupコマンド
 - $ nslookup ドメイン名 (オプション: 問い合わせ先DNSサーバーのアドレス)
##### 補足：パブリックDNSサーバー
 - nslookupコマンドでは、DNSサーバーを指定しない場合、自動的に問い合わせ先を判断してドメイン名とIPアドレスの変換を行いますが、DNSサーバーを指定することが可能です。
 - 下記は、GoogleのパブリックDNSサーバーに問い合わせを行った例を示しています。
  >ec2-user:~/environment $ nslookup google.com 8.8.8.8
  >Server:         8.8.8.8
  >Address:        8.8.8.8#53
  >
  >Non-authoritative answer:
  >Name:   google.com
  >Address: 142.251.222.46
  >Name:   google.com
  >Address: 2404:6800:4004:80f::200e
  - 自身のネットワークの接続が不安定な時などに、DNSサーバーにパブリックDNSサーバーを指定することで接続が改善されるケースがあります。
   パブリックDNSサーバーの存在は覚えておいて損は無いでしょう。