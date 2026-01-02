# Build stage
FROM golang:1.25-alpine AS builder

WORKDIR /app

# Copy Go modules and download dependencies
COPY go.mod go.sum ./
RUN go mod download

# Copy source code
COPY . .
RUN go build -o shippingservice

# Runtime stage
FROM alpine:3.18

WORKDIR /app
COPY --from=builder /app/shippingservice .

EXPOSE 8080
CMD ["./shippingservice"]
