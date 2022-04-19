# vim:set ft=dockerfile:
FROM alpine:latest

MAINTAINER Andrius Kairiukstis <andrius@kairiukstis.com>

RUN apk add --update --no-cache --quiet \
      asterisk \
    >/dev/null \
&&  rm -rf /var/cache/apk/* \
           /tmp/* \
           /var/tmp/*

RUN mkdir -p /var/spool/asterisk/fax \
&& chown -R asterisk: /var/spool/asterisk \
&& truncate -s 0 /var/log/asterisk/messages \
                 /var/log/asterisk/queue_log

EXPOSE 5060/udp 5060/tcp
VOLUME /var/lib/asterisk/sounds /var/lib/asterisk/keys /var/lib/asterisk/phoneprov /var/spool/asterisk /var/log/asterisk

ADD docker-entrypoint.sh /docker-entrypoint.sh

ENTRYPOINT ["/docker-entrypoint.sh"]
