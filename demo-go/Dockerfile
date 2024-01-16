FROM golang:1.21.6-alpine3.19 as builder
WORKDIR /app
COPY go.* .
RUN go mod tidy
COPY . .
RUN go build -o api .

FROM alpine:3.19
WORKDIR /myapp
COPY --from=builder /app/api .
CMD [ "/myapp/api" ]