FROM alpine AS build

WORKDIR /usr/local/src/geomyidae

RUN apk update && apk add build-base libressl-dev git
RUN git clone git://bitreich.org/geomyidae /usr/local/src/geomyidae
RUN make

FROM alpine

COPY --from=build /usr/local/src/geomyidae/geomyidae /usr/local/sbin/geomyidae

EXPOSE 70
CMD geomyidae -d -h 0.0.0.0
