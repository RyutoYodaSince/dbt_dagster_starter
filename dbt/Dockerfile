# dbt用Dockerfile
FROM python:3.8-slim

WORKDIR /app

# 必要なパッケージをインストール
RUN pip install dbt-snowflake
    pip install dbt-bigquery \
    dagster-dbt \
    dbt-osmosis

# dbtプロジェクトをコンテナにコピー
COPY jaffle_shop /app

CMD ["dbt", "run"]
