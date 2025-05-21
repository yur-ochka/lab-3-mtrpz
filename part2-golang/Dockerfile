FROM golang:alpine AS builder

WORKDIR /app

    go mod verify

COPY . .
RUN go build -o fizzbuzz

FROM scratch

WORKDIR /app

COPY --from=builder /app/fizzbuzz .
COPY --from=builder /app/templates/index.html templates/

EXPOSE 8080

CMD ["./fizzbuzz", "serve"]