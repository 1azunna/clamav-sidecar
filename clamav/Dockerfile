FROM alpine:3.12.1
LABEL maintainer "Azunna Ikonne <ikonnea@gmail.com>"

RUN apk add --no-cache \
    python3 py3-pip \
  && pip3 install --upgrade pip

RUN apk add --no-cache fcron clamav rsyslog wget clamav-libunrar
RUN mkdir -p /logs /data
RUN echo `date`: File created >> /logs/clamscan.log
RUN chmod +r /etc/fcron/*

COPY conf /etc/clamav
COPY start.py /start.py
COPY health.sh /health.sh
COPY scan.sh /scan.sh
RUN chmod +x /health.sh /scan.sh

CMD /start.py