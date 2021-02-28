FROM golang:1.15.0-alpine3.12 as build

WORKDIR /app

COPY . .
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 GOPROXY=https://goproxy.cn,direct go build -o main ./cmd/
# RUN chmod +x main

FROM alpine:3.12.0
COPY --from=build /app/main /

ENTRYPOINT [ "./main" ]
