FROM python:3.11

RUN apt update && apt install -y libpq-dev

COPY ./requirements.txt ./

RUN pip install -r requirements.txt

CMD mlflow server \
    --backend-store-uri postgresql+psycopg2://${POSTGRES_USER}:${POSTGRES_PASSWORD}@postgres:5432/${POSTGRES_DB} \
    --artifacts-destination s3://mlflow \
    --host 0.0.0.0 \