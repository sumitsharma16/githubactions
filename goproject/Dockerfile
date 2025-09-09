# 1. Build stage
FROM golang:1.21 AS builder

WORKDIR /app

# Copy go files
COPY . .

# Build the Go app
RUN go mod init go-docker-app && go mod tidy && go build -o server .

# 2. Runtime stage
FROM debian:bookworm-slim

WORKDIR /app

# Copy the binary from builder stage
COPY --from=builder /app/server .

# Expose port 8080
EXPOSE 8080

# Run the binary
CMD ["./server"]
