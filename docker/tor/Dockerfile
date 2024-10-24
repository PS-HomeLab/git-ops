FROM alpine:3.20.3

HEALTHCHECK CMD ["/usr/bin/curl", "--socks5", "localhost:9050", "--socks5-hostname", "localhost:9050", "https://check.torproject.org/api/ip"]

RUN apk --update --no-cache add tor \
    && rm -rf /var/cache/apk/*

COPY torrc /etc/torrc

USER "tor"

WORKDIR "/var/lib/tor"

EXPOSE 9050

ENTRYPOINT ["/usr/bin/tor", "-f", "/etc/torrc"]