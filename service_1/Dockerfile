FROM golang:1.22-alpine

WORKDIR /app

# Install curl
RUN apk add --no-cache curl

COPY . .

RUN go build -o server main.go

EXPOSE 8001

CMD ["./server"]
