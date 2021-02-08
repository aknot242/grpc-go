FROM golang:1.14-alpine AS build

WORKDIR /src/
COPY main.go go.* /src/
RUN apk add git
RUN go get google.golang.org/grpc/examples/helloworld/greeter_server
RUN CGO_ENABLED=0 go build -o /bin/greeter_server

FROM scratch
COPY --from=build /bin/greeter_server /bin/greeter_server

EXPOSE 50051

ENTRYPOINT ["/bin/greeter_server"]
