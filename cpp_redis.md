### cpp_redis 4.0.0+

https://github.com/Cylix/cpp_redis

### tacopie 3.0.0+

https://github.com/Cylix/tacopie
+++

**cpp_redis** - C++11 Lightweight Redis client: async, thread-safe, no dependency, pipelining, multi-platform.

+++

It comes with no network module, so we use default one - **tacopie**.

+++

We use `redis` as cache for indexes on storage with blocks.

+++

Usage example

```C++
cpp_redis::client client;

client.connect();

client.set("hello", "42");
client.get("hello", [] (cpp_redis::reply& reply) {
  std::cout << reply << std::endl;
});

client.sync_commit();
```
