FROM golang:1.16 As builder
ENV GO111MODULE=off
WORKDIR /app
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -ldflags '-w' -o service

FROM scratch
WORKDIR /app
COPY --from=builder /app/service .
CMD ["/app/service"]