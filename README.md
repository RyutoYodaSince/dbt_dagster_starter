# dbt_dagster_starter⭐️

このリポジトリでは、dbtとDagsterを組み合わせてデータ処理パイプラインを構築する方法を紹介しています。

## セットアップ手順

### 前提条件
- DockerとDocker Composeがインストールされていること
- Gitがインストールされていること

### プロジェクトのクローンとセットアップ

1. リポジトリをクローンします。
   ```bash
   git clone https://github.com/your-username/my_project.git
   cd my_project
   ```

2. **dbtプロジェクトの準備**  
   dbtの例として、`jaffle_shop`プロジェクトをクローンします。
   ```bash
   git clone https://github.com/dbt-labs/jaffle_shop.git dbt/jaffle_shop
   cd dbt/jaffle_shop
   ```

3. **Dagsterプロジェクトの準備**  
   Dagster用のプロジェクトをスキャフォールドします。
   ```bash
   cd ../../dagster
   dagster-dbt project scaffold --project-name my_dagster_project
   ```

4. **環境変数の設定**  
   プロジェクトルートに`.env`ファイルを作成し、必要な認証情報を追加します。
   ```bash
   # .envファイルの例

   # Snowflake認証情報
   SNOWFLAKE_ACCOUNT=your_account
   SNOWFLAKE_USER=your_user
   SNOWFLAKE_PASSWORD=your_password
   SNOWFLAKE_ROLE=your_role
   SNOWFLAKE_WAREHOUSE=your_warehouse
   SNOWFLAKE_DATABASE=your_database
   SNOWFLAKE_SCHEMA=your_schema

   # BigQuery認証情報（利用する場合はコメントを外してください）
   # BIGQUERY_PROJECT=your_project_id
   # BIGQUERY_DATASET=your_dataset
   # BIGQUERY_KEYFILE_PATH=/path/to/your/keyfile.json
   ```

5. **Docker Composeによるコンテナのビルドと起動**
   ```bash
   docker-compose up --build
   ```

6. **環境変数の設定**  
   `dbt`プロジェクトのパースを効率的に行うため、以下の環境変数を設定します。
   ```bash
   export DAGSTER_DBT_PARSE_PROJECT_ON_LOAD=1
   ```

7. **Dagsterの開発モードでの起動**  
   Dagster Web UIを開発モードで起動します。
   ```bash
   dagster dev
   ```

### GitHub ActionsのCI/CD
GitHub ActionsでのCI/CDを設定しています。
- `.github/workflows/ci.yml`で、GitHub上でのテストと検証を管理しています。

### よくあるエラーとトラブルシューティング

- **Dockerコンテナが起動しない**: 環境変数やDockerのバージョンを確認してください。
- **dbtやDagsterの認証エラー**: `.env`の認証情報が正しいか確認してください。
- **GitHub Actionsでの失敗**: CI/CDの環境変数が設定されているか確認してください。

### その他の参考情報
- [dbt Labsの公式ドキュメント](https://docs.getdbt.com/)
- [Dagsterの公式ドキュメント](https://docs.dagster.io/)


