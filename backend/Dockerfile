FROM python:3.11

WORKDIR /app

RUN apt-get update \
 && apt-get install -y python3-distutils \
 && python -m pip install --no-cache-dir --upgrade pip setuptools wheel \
 && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi:application"]