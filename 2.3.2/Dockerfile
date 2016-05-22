FROM gliderlabs/alpine:3.3
MAINTAINER Dave Finster <df@docketbook.io>

RUN apk update && \
	apk add openjdk7 bash curl && \
	cd ~ && \
	wget http://download.elastic.co/logstash/logstash/logstash-2.3.2.tar.gz && \
	tar -zxvf logstash-2.3.2.tar.gz && \
	rm logstash-2.3.2.tar.gz && \
	mv logstash-2.3.2 /logstash

ADD configurations /logstash/configurations

ENV SSL_CERT_FILE=/logstash/cacert.pem

EXPOSE 5000

ENTRYPOINT [ "/logstash/bin/logstash", "-f", "/logstash/configurations/*", "--allow-env"]