# connect-go-example

- Connectのチュートリアルを試してみる。
  https://connect.build/docs/go/getting-started/



``````
$ go run ./cmd/server/main.go
2022/09/04 23:18:55 run serve


$ curl \
>     --header "Content-Type: application/json" \
>     --data '{"name": "Jane"}' \
>     http://localhost:8080/greet.v1.GreetService/Greet
{"greeting":"Hello, Jane!"}%                              

$ grpcurl \
>     -protoset <(buf build -o -) -plaintext \
>     -d '{"name": "Jane"}' \
>     localhost:8080 greet.v1.GreetService/Greet
{
  "greeting": "Hello, Jane!"
}


$ go run ./cmd/client/main.go
2022/09/04 22:56:59 Hello, Jane!

``````