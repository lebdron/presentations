### grpc 1.7.0+

https://github.com/grpc/grpc

+++

**gRPC** - An RPC (remote procedure call) library and framework.

+++

Any interaction with `iroha` is through `gRPC`.

+++

The transmission unit in `gRPC` is `protobuf`.

+++

#### Usage

+++

1 - Define service `.proto` file:

```protobuf
message Feature {...}
message Point {...}

service RouteGuide {
   rpc GetFeature(Point) returns (Feature) {}
}
```

+++

2 - Compile `gRPC` stub with `protoc`:

```bash
$ protoc --grpc_out=. --plugin=protoc-gen-grpc=`which grpc_cpp_plugin` service.proto
$ protoc --cpp_out=. service.proto
```

+++

Result:
```bash
$ ls
service.proto
service.pb.h
service.pb.cc
service.grpc.pb.h
service.grpc.pb.cc
```

@[2](original proto file)
@[3-4](generated message classes)
@[5-6](generated implementation of service classes)

+++

3 - Write a server and client implementations.

[Official guide](https://github.com/grpc/grpc/tree/master/examples/cpp/helloworld)
