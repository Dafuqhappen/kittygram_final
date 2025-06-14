FROM python:3.11

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      build-essential python3-dev libyaml-dev \
 && rm -rf /var/lib/apt/lists/* \
 && python -m pip install --no-cache-dir \
      --upgrade pip setuptools wheel Cython gunicorn==23.0.0

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi:application"]