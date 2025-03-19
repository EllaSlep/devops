FROM python:3.9-alpine AS builder

WORKDIR /app

COPY requirements.txt .
RUN pip install --user --no-cache-dir -r requirements.txt

COPY . .

FROM python:3.9-alpine

WORKDIR /app

COPY --from=builder /root/.local /root/.local
COPY --from=builder /app /app

ENV PATH=/root/.local/bin:$PATH

RUN adduser -D myuser
USER myuser

EXPOSE 5000

CMD ["flask", "run", "--host=0.0.0.0"]