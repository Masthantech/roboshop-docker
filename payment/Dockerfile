FROM python:3.9.23-alpine3.22
EXPOSE 8080
WORKDIR /opt/server
RUN dnf install -y \
    gcc \
    gcc-c++ \
    make \
    python3-devel \
    && dnf clean all
COPY *.py .
COPY requirements.txt  .
COPY payment.ini  .
RUN pip3 install -r requirements.txt
CMD ["uwsgi", "--ini", "payment.ini"]