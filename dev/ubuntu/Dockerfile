FROM ubuntu:22.04

ARG SJP_HASH=9adccb8fe17a40252df1a3acdea7edef4633b4ecaa8ba2dd5e0270f87ae43eab

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

ADD --checksum=sha256:${SJP_HASH} \
    https://github.com/MrDave/StaticJinjaPlus/archive/refs/heads/main.tar.gz  \
    /tmp/app.tar.gz

RUN tar xzf /tmp/app.tar.gz --strip-components=1 -C /app && rm /tmp/app.tar.gz

RUN pip install -r requirements.txt

ENTRYPOINT ["python3", "main.py"]

CMD ["--srcpath=./templates", "--outpath=./build"]