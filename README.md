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






