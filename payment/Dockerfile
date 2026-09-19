FROM python:alpine3.24
EXPOSE 8080
WORKDIR /opt/server
COPY *.py .
COPY requirements.txt .
COPY payment.ini .
RUN pip3 install -r requirements.txt
CMD ["uwsgi" , "--ini", "payment.ini"]