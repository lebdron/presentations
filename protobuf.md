### protobuf 3.3.0+

https://github.com/google/protobuf
+++

Protocol Buffers (a.k.a., **protobuf**) are Google's language-neutral, platform-neutral, extensible mechanism for serializing structured data.

+++

#### Usage

+++

1 - Define `*.proto` file (schema):

```protobuf
syntax 'proto3';
package api;

message Person {
  string name = 1;
  int32  age  = 2;
}
```

+++

2 - Compile it with `protoc` for [your language](https://developers.google.com/protocol-buffers/):

```bash
$ protoc --cpp_out=. myproto.proto
$ ls
myproto.proto
myproto.pb.h
myproto.pb.cc
```

+++

3 - Include it and use:

```C++
Person john;
fstream input(argv[1], ios::in | ios::binary);
john.ParseFromIstream(&input);
std::string name = john.name();
int age = john.age();
```

+++

Any interaction with `iroha` is through its public API, which sends and receives protocol buffers.

+++

List of all `proto` files can be found at `schema` folder:

```bash
$ ls
block.proto     endpoint.proto  peer_service.proto  responses.proto
CMakeLists.txt  loader.proto    primitive.proto     yac.proto
commands.proto  ordering.proto  queries.proto
```
