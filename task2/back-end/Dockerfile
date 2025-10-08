FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive

# System Python + venv
RUN apt-get update \
 && apt-get upgrade -y \
 && apt-get install -y python3 python3-venv python3-pip ca-certificates curl \
 && rm -rf /var/lib/apt/lists/*

# Isolated virtualenv so pip installs cleanly
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:${PATH}"

# Python deps in venv (Flask must be via pip)
RUN pip install --upgrade pip setuptools wheel \
 && pip install flask

WORKDIR /app
COPY api.py /app/api.py

EXPOSE 5252
CMD ["python", "/app/api.py"]
