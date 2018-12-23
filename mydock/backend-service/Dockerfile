FROM golang:1.8

WORKDIR $GOPATH/src/github.com/ServiceComputing1/server
COPY . $GOPATH/src/github.com/ServiceComputing1/

RUN go get -d -v ./...
RUN  go build .

EXPOSE  8080
 
ENTRYPOINT  ["./server"]

#CMD ["go","run","./main.go"]

#RUN go install -v ./...