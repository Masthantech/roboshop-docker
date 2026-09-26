FROM python:3.9
WORKDIR /opt/server
#COPY *.py .
COPY requirements.txt .
#COPY payment.ini .
# Install build dependencies
RUN apk add --no-cache python3-dev build-base linux-headers pcre-dev
RUN pip3 install  --prefix=/install -r requirements.txt



FROM python:3.9.23-alpine3.22
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /opt/server
COPY --from=builder /install /usr/local
COPY *.py . 
COPY payment.ini .
USER roboshop 
CMD ["uwsgi", "--ini", "payment.ini"]


# FROM python:3.9
# EXPOSE 8080
# WORKDIR /opt/server
# COPY *.py .
# COPY requirements.txt  .
# COPY payment.ini  .
# RUN pip3 install -r requirements.txt
# CMD ["uwsgi", "--ini", "payment.ini"]