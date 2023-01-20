FROM golang:alpine AS builder

WORKDIR webserver
COPY ./dispatcher.go .
RUN go build dispatcher.go

FROM alpine
#RUN mkdir -p /webserver/
WORKDIR webserver
COPY --from=builder /go/webserver/dispatcher /webserver/
COPY . . 
EXPOSE 80
#pour assurer la réponse au ctl-c

CMD ["/webserver/dispatcher"]


