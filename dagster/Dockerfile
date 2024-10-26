# Dagster用Dockerfile
FROM python:3.8-slim

WORKDIR /app

# 必要なパッケージをインストール
RUN pip install dagster dagit dagster-dbt

# Dagsterプロジェクトをコンテナにコピー
COPY my_dagster_project /app

# DagsterのWeb UIをポート3000で起動
CMD ["dagit", "-h", "0.0.0.0", "-p", "3000"]
