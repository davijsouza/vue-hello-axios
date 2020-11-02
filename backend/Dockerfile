FROM python:3.6-alpine

WORKDIR /app

COPY supervisord.conf /etc/supervisord.conf
COPY . /app

RUN apk add supervisor \
    && pip install -r requirements.txt

CMD ["supervisord", "-c", "/etc/supervisord.conf"]    

