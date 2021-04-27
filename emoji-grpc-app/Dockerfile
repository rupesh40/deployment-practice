FROM golang:latest

WORKDIR /emoji-app

COPY go.mod .

COPY go.sum .

RUN go mod download

COPY . .

RUN go build 

CMD [ "./emoji-grpc-app.exe" ] 