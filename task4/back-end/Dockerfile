FROM ubuntu:latest
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
 && apt-get upgrade -y \
 && apt-get install -y python3 python3-venv python3-pip ca-certificates curl \
 && rm -rf /var/lib/apt/lists/*
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:${PATH}"
RUN pip install --upgrade pip setuptools wheel \
 && pip install flask flask-cors
WORKDIR /app
COPY api.py /app/api.py
EXPOSE 5252
CMD ["python", "/app/api.py"]
