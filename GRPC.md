gRPC is a technology to allow calling server functions from a client,
possibly from a different system. For an overview of gRPC and protocol
buffers see the [official gRPC docs **gRPC
overview**](https://grpc.io/docs/guides/index.html).

This page lists third party gRPC applications and afterwards provides
development resources.

## Applications

  - [murmur-cli](https://github.com/layeh/murmur-cli) - manage a
    grpc-enabled murmur server from the command-line

## Sample application (Go)

The goal of this guide is to familiarize yourself with the
[gRPC](http://www.grpc.io/) Mumble interface. This will be done by
implementing a sample application in [Go](https://golang.org/). Our
finished application will allow users to trigger a nudge command on
other users that sends the user a predefined message.

This guide assumes you have the following things:

  - A Unix-like system, such as Linux or Mac OS X, with a terminal.
  - A running murmur server that has been compiled with gRPC support.
  - A Go installation and an understanding of how to write and run Go
    code.
  - The [Google Protocol
    Buffer](https://developers.google.com/protocol-buffers/) compiler
    installed.

Create and open a new folder that will hold our project's code:

`mkdir murmur-nudge`
`cd murmur-nudge`

We need to install the required Go libraries using the \`go get\` tool.
Thee below commands will install the gRPC and protocol buffer libraries,
respectively.

`go get -u google.golang.org/grpc`
`go get -u github.com/golang/protobuf/{proto,protoc-gen-go}`

Like any other project that uses protocol buffers, we need to a copy of
the .proto file for code generation. We will now download the Murmur
gRPC protocol buffer file into the current directory.

`wget `<https://raw.githubusercontent.com/mumble-voip/mumble/master/src/murmur/MurmurRPC.proto>

(This address if for the master branch. You may want to use a version
specific file.)

The protocol buffer file now needs to be compiled into our target
programming language (in our case, Go). The code will be generated using
the `protoc` program provided by the Protocol Buffer package. The
compiled code should be stored it its own directory, so that will be
created first.

`mkdir MurmurRPC`
`protoc -I. --plugin=$GOPATH/bin/protoc-gen-go --go_out=plugins=grpc:MurmurRPC MurmurRPC.proto`

The above command should have created a file named `MurmurRPC.pb.go` in
the `MurmurRPC` directory.

In your code editor, create a new file called `nudge.go` in the project
directory.

The first thing we need to do in that file is create a connection to our
murmur server. We can do this with the
[`grpc.Dial`](https://godoc.org/google.golang.org/grpc#Dial) function.

`package main`

`import (`
`   "google.golang.org/grpc"`
`)`

`func main() {`
`   conn, err := grpc.Dial("127.0.0.1:50051", grpc.WithInsecure())`
`   if err != nil {`
`       panic(err)`
`   }`
`   defer conn.Close()`
`}`

If you run the above program (`go run nudge.go`), it should start then
exit without error, meaning a connection was established.

Once a connection has been established, we can use code in the generated
`.pb.go` file to invoke RPC methods on the server. We will be using two
RPC methods: `ServerEvents`, a stream of events that happen on a server,
and; `ContextActionAdd`, adds a context action to a given user. Using
those two methods, we can add a context action to a user joining the
server.

`package main`

`import (`
`   `**`"log"`**

`   `**`"./MurmurRPC"`**

`   `**`"github.com/golang/protobuf/proto"`**
`   `**`"golang.org/x/net/context"`**
`   "google.golang.org/grpc"`
`)`

`func main() {`
`   `**`log.Println("Nudge``   ``starting")`**

`   conn, err := grpc.Dial("127.0.0.1:50051", grpc.WithInsecure())`
`   if err != nil {`
`       panic(err)`
`   }`
`   defer conn.Close()`

`   `**`server``   ``:=``   ``&MurmurRPC.Server{`**
`       `**`Id:``   ``proto.Uint32(1),`**
`   `**`}`**

`   `**`streamClient``   ``:=``   ``MurmurRPC.NewV1Client(conn)`**
`   `**`caClient``   ``:=``   ``MurmurRPC.NewV1Client(conn)`**
`   `**`stream,``   ``err``   ``:=``
 ``streamClient.ServerEvents(context.Background(),``   ``server)`**
`   `**`if``   ``err``   ``!=``   ``nil``   ``{`**
`       `**`panic(err)`**
`   `**`}`**
`   `**`for``   ``{`**
`       `**`event,``   ``err``   ``:=``   ``stream.Recv()`**
`       `**`if``   ``err``   ``!=``   ``nil``   ``{`**
`           `**`break`**
`       `**`}`**
`       `**`if``   ``event.GetType()``   ``!=``
 ``MurmurRPC.Server_Event_UserConnected``   ``{`**
`           `**`continue`**
`       `**`}`**
`       `**`log.Printf("Added``   ``context``   ``action``   ``to``
 ``%s\n",``   ``event.GetUser().GetName())`**
`       `**`caClient.ContextActionAdd(context.Background(),``
 ``&MurmurRPC.ContextAction{`**
`           `**`Server:``   ``server,`**
`           `**`Context:``
 ``proto.Uint32(uint32(MurmurRPC.ContextAction_User)),`**
`           `**`Action:``   ``proto.String("nudge"),`**
`           `**`Text:``   ``proto.String("Nudge!"),`**
`           `**`User:``   ``event.GetUser(),`**
`       `**`})`**
`   `**`}`**
`}`

There are a couple of things to note in the lines we added above. First,
we create a `MurmurRPC.Server` whose ID is 1; this is the default
virtual server. If you have a another virtual server you would like to
operate on, replace 1 with its ID. Second, we create two clients using
`MurmurRPC.NewV1Client` (`streamClient` and `caClient`). This is
required as a client can only handle 1 simultaneous request. In our
case, the `ServerEvents` is still active when `ContextActionAdd`, so we
need another client.

If you run the program now, each user that connects to the server will
see a "Nudge\!" action in the right-click menu of any user. Users will
notice that clicking on the "Nudge\!" action will not do anything. To
change that, we need to create a listener that receives a notification
whenever an action is triggered.

`package main`

`import (`
`   "log"`

`   "./MurmurRPC"`

`   "github.com/golang/protobuf/proto"`
`   "golang.org/x/net/context"`
`   "google.golang.org/grpc"`
`)`

`func main() {`
`   log.Println("Nudge starting")`

`   conn, err := grpc.Dial("127.0.0.1:50051", grpc.WithInsecure())`
`   if err != nil {`
`       panic(err)`
`   }`
`   defer conn.Close()`

`   server := &MurmurRPC.Server{`
`       Id: proto.Uint32(1),`
`   }`

`   `**`go``   ``func()``   ``{`**
`       streamClient := MurmurRPC.NewV1Client(conn)`
`       caClient := MurmurRPC.NewV1Client(conn)`
`       stream, err := streamClient.ServerEvents(context.Background(), server)`
`       if err != nil {`
`           panic(err)`
`       }`
`       for {`
`           event, err := stream.Recv()`
`           if err != nil {`
`               break`
`           }`
`           if event.GetType() != MurmurRPC.Server_Event_UserConnected {`
`               continue`
`           }`
`           log.Printf("Added context action to %s\n", event.GetUser().GetName())`
`           caClient.ContextActionAdd(context.Background(), &MurmurRPC.ContextAction{`
`               Server:  server,`
`               Context: proto.Uint32(uint32(MurmurRPC.ContextAction_User)),`
`               Action:  proto.String("nudge"),`
`               Text:    proto.String("Nudge!"),`
`               User:    event.GetUser(),`
`           })`
`       }`
`   `**`}()`**

`   `**`msgClient``   ``:=``   ``MurmurRPC.NewV1Client(conn)`**
`   `**`caClient``   ``:=``   ``MurmurRPC.NewV1Client(conn)`**
`   `**`stream,``   ``err``   ``:=``
 ``caClient.ContextActionEvents(context.Background(),``
 ``&MurmurRPC.ContextAction{`**
`       `**`Server:``   ``server,`**
`       `**`Action:``   ``proto.String("nudge"),`**
`   `**`})`**
`   `**`if``   ``err``   ``!=``   ``nil``   ``{`**
`       `**`panic(err)`**
`   `**`}`**
`   `**`for``   ``{`**
`       `**`event,``   ``err``   ``:=``   ``stream.Recv()`**
`       `**`if``   ``err``   ``!=``   ``nil``   ``{`**
`           `**`break`**
`       `**`}`**
`       `**`if``   ``event.GetUser()``   ``==``   ``nil``   ``{`**
`           `**`continue`**
`       `**`}`**
`       `**`actor,``   ``err1``   ``:=``
 ``msgClient.UserGet(context.Background(),``   ``event.GetActor())`**
`       `**`user,``   ``err2``   ``:=``
 ``msgClient.UserGet(context.Background(),``   ``event.GetUser())`**
`       `**`if``   ``err1``   ``!=``   ``nil``   ``||``   ``err2``
 ``!=``   ``nil``   ``{`**
`           `**`continue`**
`       `**`}`**
`       `**`if``   ``actor.GetSession()``   ``==``
 ``user.GetSession()``   ``{`**
`           `**`msgClient.TextMessageSend(context.Background(),``
 ``&MurmurRPC.TextMessage{`**
`               `**`Server:``   ``server,`**
`               `**`Users:``   ``[]*MurmurRPC.User{actor},`**
`               `**`Text:``   ``proto.String("Cannot``   ``nudge``
 ``yourself!"),`**
`           `**`})`**
`           `**`continue`**
`       `**`}`**
`       `**`log.Printf("%s``   ``nudged``   ``%s\n",``
 ``actor.GetName(),``   ``user.GetName())`**
`       `**`msg``   ``:=``   ``&MurmurRPC.TextMessage{`**
`           `**`Server:``   ``server,`**
`           `**`Users:``   ``[]*MurmurRPC.User{user},`**
`           `**`Text:``   ``proto.String(actor.GetName()``   ``+``
 ``"``   ``nudged``   ``you!"),`**
`       `**`}`**
`       `**`for``   ``i``   ``:=``   ``1;``   ``i``   ``<=``   ``3;``
 ``i++``   ``{`**
`           `**`msgClient.TextMessageSend(context.Background(),``
 ``msg)`**
`       `**`}`**
`   `**`}`**
`}`

You will notice in the above modifications that the `ServerEvents`
stream was placed in its own Go routine. This is done to allow the
server event listener to run at the same time as the context action
listener.

The usage of `UserGet` might seem strange, since the context action
actor and user are already part of the event. However, if you were to
inspect either `event.Actor` or `event.User`, you would notice that only
the user's server and session would be set. This is a bandwidth saving
technique: embedded messages sometimes only contain enough identifying
information to request more information via an RPC call. You should
refer to the protocol buffer comments to see where this applies.

And that's it\! Running the above, completed program will allow your
users to nudge other users on the server.

[Category:Documentation
English](Category:Documentation_English "wikilink") [Category:Mumble
Server](Category:Mumble_Server "wikilink")