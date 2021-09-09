FROM golang:1.16-alpine AS build-env
WORKDIR /app
COPY . .
RUN go test ./common/common_test.go && go build

FROM golang:1.16-alpine
EXPOSE 8080
WORKDIR /usr/src/app
COPY --from=build-env /app/server ./server
RUN adduser -D appuser
USER appuser
CMD ["./server"]