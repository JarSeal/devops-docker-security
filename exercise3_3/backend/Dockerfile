FROM golang:1.16-alpine

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

RUN go test ./common/common_test.go

RUN go build

RUN adduser -D appuser
USER appuser

CMD ["./server"]