FROM golang:alpine AS builder

WORKDIR /go/src/app
ADD ./app /go/src/app
RUN go mod init
RUN go get -d -v
RUN go build -o app
RUN GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" -o /go/src/app


FROM scratch
COPY --from=builder /go/src/app /usr/bin
ENTRYPOINT ["app"]
CMD ["bash"]