FROM python:3.7 AS builder

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

# done lib part installation

FROM python:3.7-slim

WORKDIR /app

COPY --from=builder /usr/local/lib/python3.7/site-packages/ /usr/local/lib/python3.7/site-packages/

COPY . .

ENTRYPOINT [ "python","run.py" ]