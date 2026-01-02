# Use official Golang image to build the app
FROM golang:1.25-alpine AS builder

WORKDIR /app
COPY . .
RUN go build -o productcatalogservice .

# Use lightweight image for runtime
FROM alpine:3.18
WORKDIR /app
COPY --from=builder /app/productcatalogservice .
EXPOSE 3550
CMD ["./productcatalogservice"]
