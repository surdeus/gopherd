FROM debian AS build

WORKDIR /usr/local/src/geomyidae

RUN apt-get update && apt-get install -y gcc make git
RUN git clone git://bitreich.org/geomyidae /usr/local/src/geomyidae
# Debian sucks at LibreSSL. Maybe find some other base image?
RUN make TLS_CFLAGS= TLS_LDFLAGS=

FROM debian

ENV HOST 0.0.0.0

COPY --from=build /usr/local/src/geomyidae/geomyidae /usr/local/sbin/geomyidae

EXPOSE 70
CMD geomyidae -d -h $HOST
