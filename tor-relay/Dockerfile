FROM alpine:latest
LABEL maintainer "Jessie Frazelle <jess@linux.com>"

RUN apk --no-cache add \
    bash \
    tor
	
COPY torrc.bridge torrc.middle torrc.exit /etc/tor/

COPY entrypoint.sh /entrypoint.sh
RUN chmod ugo+rx /entrypoint.sh

RUN chown -R tor /etc/tor
USER tor

RUN mkdir /var/lib/tor/.tor
VOLUME /var/lib/tor/.tor
RUN chown -R tor /var/lib/tor/.tor

ENTRYPOINT [ "/entrypoint.sh" ]
