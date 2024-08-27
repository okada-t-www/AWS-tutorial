# AWS-tutorial
このリポジトリは、わたしがAWSインフラ業務に入る前の準備内容をまとめたものです。AWSの基本的なサービス、ツール、ベストプラクティスなどリンクや手順を随時記録していきます。

## 参考情報
- [AWS ドキュメント](https://docs.aws.amazon.com/ja_jp/?nc2=h_ql_doc_do)
- [AWS 用語集](https://docs.aws.amazon.com/glossary/latest/reference/glos-chap.html)
- [AWS 日本語ハンズオン](https://aws-samples.github.io/jp-contents-hub/)
- [公式webマガジン_builders.flash 最新記事一覧](https://aws.amazon.com/jp/builders-flash/all-list/?awsf.filter-name=*all)
- [The Amazon Builders' Library_どのように構築し、運用するのか](https://aws.amazon.com/jp/builders-library/?cards-body.sort-by=item.additionalFields.sortDate&cards-body.sort-order=desc&awsf.filter-content-category=*all&awsf.filter-content-type=*all&awsf.filter-content-level=*all)
-  [2023-03-02_サーバーレスのローカル開発環境を整備する ~前編](https://aws.amazon.com/jp/builders-flash/202303/serverless-local-dev-environment/)
- [2021-01-05 サーバーレスの勉強方法を聞いてみた](https://aws.amazon.com/jp/builders-flash/202101/way-to-learn-serverless/)

## Chatgpt曰く
AWSインフラを担当する予定であれば、以下のポイントに注目して準備を進めると良いでしょう。AWSインフラの設定や管理は、クラウドリソースの効率的な利用やシステムの拡張性を確保するために重要です。

1. 基本的なAWSサービスの理解
まずは、AWSの主要なサービスについて理解を深めることが重要です。

- Amazon EC2 (Elastic Compute Cloud):
  仮想サーバーを提供するサービスで、スケーラブルなコンピューティングリソースを実現します。
- Amazon S3 (Simple Storage Service):
  オブジェクトストレージサービスで、データの保存やバックアップに利用されます。
- Amazon RDS (Relational Database Service):
  マネージドなリレーショナルデータベースを提供し、データベースの管理を簡素化します。
- AWS IAM (Identity and Access Management):
  ユーザーやリソースへのアクセス制御を行い、セキュリティを確保します。
- Amazon VPC (Virtual Private Cloud):
  仮想ネットワークを構築し、セキュアなクラウド環境を作成します。

2. AWSインフラストラクチャの設計
AWSインフラの設計では、以下の要素に注意を払います。
- アーキテクチャの選択:
  スケーラブルで高可用性なアーキテクチャを設計します。負荷分散やオートスケーリングを活用して、システムの可用性を高めます。
- セキュリティ:
  IAMを用いたアクセス制御や、AWS Security Groupsによるネットワークレベルのセキュリティを確保します。
- バックアップとリカバリ:
  データのバックアップ戦略を策定し、災害復旧プランを準備します

3. AWSマネジメントコンソールとCLIの使用
AWSの操作には、マネジメントコンソールとCLI（コマンドラインインターフェース）を使用します。

- マネジメントコンソール:
  AWSサービスの設定や監視を視覚的に行えます。初心者にとっては直感的で使いやすいです。
- AWS CLI:
  自動化スクリプトやデプロイメントパイプラインでの使用に便利で、大規模な操作を効率化します。

4. インフラ自動化とIaC (Infrastructure as Code)
インフラの自動化は、リソース管理を効率化し、エラーを減らすために重要です。

- AWS CloudFormation:
  インフラをコードで定義し、テンプレートを使用して環境を迅速に展開できます。
- Terraform:
  サードパーティのIaCツールで、AWSを含む複数のクラウドプロバイダに対応しています。

5. モニタリングと最適化
AWS環境を監視し、最適化することでパフォーマンスとコストを管理します。

- Amazon CloudWatch:
  リソースの監視やログ管理を行い、アラームを設定して異常を検知します。
- AWS Cost Explorer:
  コスト分析を行い、費用を最適化します。

6. 学習リソースの活用
AWSインフラに関する知識を深めるための学習リソースを活用します。

- AWS公式トレーニング:
  AWS Training and Certificationで、インフラストラクチャ関連のコースを受講します。
- オンラインコース:
  CourseraやUdemyなどで提供されているAWSインフラ関連のコースを受講します。
  これらのポイントに注目して、AWSインフラの設定と管理に必要なスキルを身につけていくことができます。準備を進めながら、実際のプロジェクトでの経験を積んでください。

  ## サーバレスのローカル環境構築（実践編）
  - 概要図
    ![image](https://github.com/user-attachments/assets/e11c85f2-faf1-467b-bc2a-99fa78f30f28)

### 事前にやっていること：
- WSL開発環境とHomebrew（macOS で広く利用されるパッケージマネージャーのこと）のセットアップ
  [Homebrewとは](https://brew.sh/ja/)

- AWS CLIのインストール
```bash
brew install awscli
```
- バージョン情報(2024/08/01)
```bash
 aws --version
aws-cli/2.17.19 Python/3.11.9 Linux/5.15.133.1-microsoft-standard-WSL2 source/x86_64.ubuntu.22
```

### ローカル環境整備
- AWS SAM CLIのインストール
```bash
brew tap aws/tap
brew install aws-sam-cli
```

- VSコードにてAWS Toolkitをインストール
  ![image](https://github.com/user-attachments/assets/29fb4f04-5039-444d-8dff-e1a028a95381)

  - AWS 認証情報の用意
![image](https://github.com/user-attachments/assets/cfc35e69-cf89-4ea4-a5c8-175622d16129)
⇒AWS 認証情報 (アクセスキー ID / シークレットキー) を生成・ダウンロード

  - コマンドラインにて以下を実行する
  ```bash
  $aws configure --profile 実施AWSユーザ名
  ```
  アクセスキー、シークレットアクセスキー、リージョン、表示形式（Json or csv）を選択してEnter押下

  - ユーザ一覧取得(Tokyoリージョン)
  ```bash
  $ aws iam list-users --region ap-northeast-1 --profile 実施AWSユーザ名
  ```

  - SAM CLIを用いてテンプレートを選択する
  ```bash
  $ sam init
  ```
  - プロジェクトのひな形 一覧
    引用：[2023-03-13 サーバーレスのローカル開発環境を整備する ~中編](https://aws.amazon.com/jp/builders-flash/202303/serverless-local-dev-environment-2/)
    
| Template                                | Java          | .NET      | Go   | Node.js       | Python                  | Ruby | Rust | サーバーレスパターンの関連するケース                     | コメント                                   |
|-----------------------------------------|---------------|-----------|------|---------------|-------------------------|------|------|--------------------------------------------------|--------------------------------------------|
| VS Code                                 | SAM CLI テンプレートの一部と同じ。コメント部の appTemplate で判別可能。  |           |      |               |                         |      |      | (シンプルな API)                               | hello-world                                |
| SAM Hello World                         | 11, 8         | 6, 5, 3.1 | 1.x  | 18, 16, 14, 12 | 3.10, 3.9, 3.8, 3.7     |      |      | (シンプルな API)                               | hello-world                                |
| SAM CLI                                 | -1 と同じ     |           |      |               |                         |      |      |                                                  |                                            |
| EventBridge Hello World                 |               |           | 1.x  |               | 3.10, 3.9, 3.8, 3.7     |      |      | スケジュール・ジョブ/SaaSイベント                   | eventbridge-hello-app                      |
| SAM CLI                                 | -8 のうちの一つ |           |      |               |                         |      |      |                                                  |                                            |
| EventBridge App From Scratch            |               |           | 1.x  |               | 3.10, 3.9, 3.8, 3.7     |      |      | スケジュール・ジョブ/SaaSイベント                   | eventbridge-scheme-app                     |
| SAM CLI                                 | -8 のうちの一つ |           |      |               |                         |      |      |                                                  |                                            |
| Step Functions Sample                   | 11, 8         | 6, 3.1    | 1.x  | 18, 16, 14, 12 | 3.10, 3.9, 3.8, 3.7     |      |      | アプリケーションフロー処理                         | step-functions-sample-app                 |
| SAM CLI                                 | -4 と同じ     |           |      |               |                         |      |      |                                                  |                                            |
| App Backend using TypeScript            |               |           |      | 12            |                         |      |      |                                                  | quick-start-typescript-app                |
| Eclipse                                 | 注: Eclipse 2021-12 以前でのみ機能します |           |      |               |                         |      |      |                                                  |                                            |
| article                                 | x             |           |      |               |                         |      |      | 動的 Web / モバイルバックエンド                    |                                            |
| hello-world                             | x             |           |      |               |                         |      |      | (単独のLambda関数)                             |                                            |
| recognition                              | x             |           |      |               |                         |      |      | 画像処理 / シンプルなデータ加工                     |                                            |
| IntelliJ / Rider                        | 多くは SAM CLI テンプレートの一部と同じ。 |           |      |               |                         |      |      |                                                  |                                            |
| SAM Hello World                         | 17, 11, 8     | 6, 3.1    |      | 18, 16, 14    | 3.11, 3.10, 3.9, 3.8, 3.7 |      |      | （シンプルな API）                              | hello-world                                |
| SAM CLI                                 | -1 と同じ     |           |      |               |                         |      |      |                                                  |                                            |
| EventBridge Hello World                 | 17, 11, 8     |           |      |               | 3.11, 3.10, 3.9, 3.8, 3.7 |      |      | スケジュール・ジョブ/SaaSイベント                   | eventbridge-hello-app                      |
| SAM CLI                                 | -8 のうちの一つ |           |      |               |                         |      |      |                                                  |                                            |
| EventBridge App From Scratch            | 17, 11, 8     |           |      |               | 3.11, 3.10, 3.9, 3.8, 3.7 |      |      | スケジュール・ジョブ/SaaSイベント                   | eventbridge-scheme-app                     |
| SAM CLI                                 | -8 のうちの一つ |           |      |               |                         |      |      |                                                  |                                            |
| DynamoDB Event Example                  |               |           |      |               | 3.11, 3.10, 3.9, 3.8, 3.7 |      |      | データ変更トリガー処理                           | aws-samples/cookiecutter-aws-sam-dynamodb-python |
| SAM CLI                                 | useCaseName で判別可能。 |           |      |               |                         |      |      |                                                  |                                            |
| 1 - Hello World Example                 | 17, 11, 8     | 7, 6      | 1.x  | 18, 16, 14    | 3.11, 3.10, 3.9, 3.8, 3.7 | 3.2, 2.7 | x    | （シンプルな API）                              |                                            |
| 2 - Data processing                     |               | 6         |      | 18, 16, 14    |                         |      |      | シンプルなデータ加工、イベント駆動の業務処理連携      |                                            |
| 3 - Hello World Example with Powertools | 17, 11, 8     | 6         |      | 18, 16, 14    | 3.10, 3.9, 3.8, 3.7     |      |      | （シンプルな API）                              |                                            |
| 4 - Multi-step workflow                | 17, 11, 8     | 6         | 1.x  | 18, 16, 14    | 3.11, 3.10, 3.9, 3.8, 3.7 | 3.2, 2.7 |      | アプリケーションフロー処理                         |                                            |
| 5 - Scheduled task                      |               | 6         |      | 18, 16, 14    |                         |      |      | スケジュール・ジョブ                              |                                            |
| 6 - Standalone function                |               | 6         |      | 18, 16, 14    |                         |      |      | （単独のLambda関数）                            |                                            |
| 7 - Serverless API                     |               | 6         |      | 18, 16, 14    |                         |      |      | 動的 Web / モバイルバックエンド                    |                                            |
| 8 - Infrastructure event management     | 17, 11, 8     |           | 1.x  |               | 3.11, 3.10, 3.9, 3.8, 3.7 |      |      | スケジュール・ジョブ/SaaSイベント                   |                                            |
| 9 - Lambda Response Streaming           |               |           | 1.x  | 18, 16        |                         |      |      | Response Streaming 機能 + Function URLs のサンプル |                                            |
| 10 - Serverless Connector Hello World Example |               |           |      | 16, 14        | 3.11, 3.10, 3.9, 3.8, 3.7 |      |      | (シンプルな API)                              | SAM Connector 利用のサンプル                |
| 11 - Multi-step workflow with Connectors |               |           |      | 16, 14        | 3.11, 3.10, 3.9, 3.8, 3.7 |      |      | アプリケーションフロー処理                        | SAM Connector 利用のサンプル                |
| 12 - GraphQLApi Hello World Example     |               |           |      | 18            |                         |      |      | インタラクティブ API                             | AppSync を利用したサンプル                 |
| 13 - Full Stack                         |               |           |      | 18            |                         |      |      | 動的 Web / モバイルバックエンド                    | フロント UI 部を含む、サーバーレス Web アプリのフルスタック |
| 14 - Lambda EFS example                 |               |           |      |               | 3.11, 3.10, 3.9, 3.8     |      |      |                                                  | EFS 利用サンプル                            |
| 15 - Hello World Example With Powertools |               |           |      |               | 3.11                    |      |      | (シンプルな API)                              |                                            |
| 16 - DynamoDB Example                   |               |           |      |               |                         |      | x    | (シンプルな API)                              | Rust 実装例のシンプルな Data Put API      |
| 17 - Machine Learning                   |               |           |      |               | 3.11, 3.10, 3.9, 3.8     |      |      | (機械学習推論API)                              |                                            |

- プロジェクトインストール後イメージ

![image](https://github.com/user-attachments/assets/cea4d7a8-40b6-43b8-9ae1-75fa580a68a7)

- パイプラインのセットアップ

目的：サーバーレスアプリケーションをデプロイするための CI/CD パイプラインの設定ファイルを生成する
  




↑つづきは今度↑



## 8/2 CloudTrail 触ってみて

- 概要
  AWSアカウントに対してだれがいつ何をしたかを確認することができるサービス
- やりたいこと（8/2午後～）
  ユーザーごとにログをフィルターして、それぞれ何をやってるか記録する

  ### 手段の調査
  ・S3＋Athena、AWS Glueクローラー
  ![image](https://github.com/user-attachments/assets/2eeb6b64-89ac-42f7-9567-9764885bc5f4)

  





    

    







