
FROM golang:1.23.8 as builder
RUN mkdir /build
ADD . /build/
WORKDIR /build
RUN make build-apiserver
FROM alpine
RUN apk --no-cache add ca-certificates
RUN adduser -S -D -H -u 3454 -h /app octelium
USER octelium
COPY --from=builder /build/bin/octelium-apiserver /app/
EXPOSE 8080
ENTRYPOINT ["/app/octelium-apiserver"]

