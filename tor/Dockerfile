FROM alpine:latest

RUN apk update
RUN apk upgrade
RUN apk add tor
RUN rm /var/cache/apk/*

ADD ./torrc /etc/tor/torrc
USER tor
CMD /usr/bin/tor -f /etc/tor/torrc
EXPOSE 9150