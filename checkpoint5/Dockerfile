FROM golang:1.17
RUN mkdir /app
ADD . /app/
RUN go env -w GO111MODULE=on
RUN go env -w GOPROXY="https://goproxy.cn,direct"
WORKDIR /app/
RUN go mod tidy
RUN go build main.go
CMD ["./main"]