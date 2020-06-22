FROM golang:alpine

# Install Alpine Dependencies
RUN apk update && apk upgrade && \
    apk add --no-cache git make cmake

WORKDIR /build
COPY go.mod .
COPY go.sum .
RUN go get -u -v all 

COPY main.go .
COPY Makefile .
RUN make build 

WORKDIR /dist

RUN cp /build/demo.bin .

# Export necessary port
EXPOSE 8080

CMD ["/dist/demo.bin"]