# Use official Go image
FROM golang:1.22-alpine

# Set working directory inside container
WORKDIR /app

# Copy go.mod and source code
COPY go.mod ./
COPY . .

# Download dependencies
RUN go mod tidy

# Build the Go app
RUN go build -o server

# Expose the port your Go server listens on
EXPOSE 8088

# Run the server
CMD ["./server"]
