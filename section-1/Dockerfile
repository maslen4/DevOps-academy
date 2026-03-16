# ---------------- Build stage -----------------
FROM python:3.11-slim AS builder

WORKDIR /install

COPY requirements.txt .

RUN pip install --prefix=/install -r requirements.txt


# ----------- Runtime stage -------------

FROM python:3.11-slim

WORKDIR /app

COPY --from=builder /install /usr/local
COPY src/app.py .

EXPOSE 5000

CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]