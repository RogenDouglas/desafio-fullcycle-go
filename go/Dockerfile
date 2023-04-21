FROM golang:alpine AS builder

WORKDIR /go/app

COPY go.mod ./
RUN go mod download && go mod verify

COPY *.go ./

RUN GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" -o /fullcycle

FROM scratch

COPY --from=builder /fullcycle /fullcycle

CMD [ "/fullcycle" ]