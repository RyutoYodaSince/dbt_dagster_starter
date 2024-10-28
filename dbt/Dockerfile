# dbt用Dockerfile
FROM python:3.8-slim

WORKDIR /app

# 必要なパッケージをインストール
RUN pip install dbt-bigquery dbt-snowflake dagster-dbt dbt-osmosis

# dbtプロジェクトをコンテナにコピー
COPY jaffle_shop /app

CMD ["dbt", "run"]
