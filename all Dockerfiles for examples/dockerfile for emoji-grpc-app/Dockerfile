FROM golang:1.11 as builder
WORKDIR /my-grpc
COPY go.mod .
COPY go.sum .
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -v -o emoji-service main.go

FROM scratch
WORKDIR /bin/
COPY --from=builder /my-grpc/emoji-service .
ENTRYPOINT [ "/bin/emoji-service" ]
CMD [ "9000" ]
EXPOSE 9000