
# FROM python:3.9
# EXPOSE 8080
# WORKDIR /opt/server
# COPY *.py .
# COPY requirements.txt  .
# COPY payment.ini  .
# RUN pip3 install -r requirements.txt
# CMD ["uwsgi", "--ini", "payment.ini"]


FROM python:3.9.25-alpine3.22 AS builder
WORKDIR /app
COPY requirements.txt .
RUN apk add --no-cache --virtual .build-deps gcc musl-dev linux-headers \
    && pip3 install --prefix=/install -r requirements.txt \
    && apk del .build-deps

FROM python:3.9.25-alpine3.22
WORKDIR /app
EXPOSE 8080
ENV CART_HOST:"cart" \
    CART_PORT:"8080" \
    USER_HOST:"user" \
    USER_PORT:"8080" \
    AMQP_HOST:"rabbitmq" \
    AMQP_USER:"roboshop" \
    AMQP_PASS:"roboshop123"
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY  --from=builder /install /usr/local
COPY --chown=roboshop:roboshop payment.ini *.py requirements.txt .
USER roboshop
CMD ["uwsgi", "--ini", "payment.ini"]

















