FROM alpine:3.24

RUN apk add --no-cache unbound

RUN unbound-anchor -v -a /etc/unbound/root.key

COPY unbound.conf /etc/unbound/unbound.conf
RUN unbound-checkconf /etc/unbound/unbound.conf \
    && chown -R unbound:unbound /etc/unbound

EXPOSE 53/tcp 53/udp

ENTRYPOINT ["/usr/sbin/unbound", "-d"]
