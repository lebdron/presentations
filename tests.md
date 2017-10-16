### gtest, gmock 1.7.0+

https://github.com/google/googletest

### gbenchmark v1.2.0+

https://github.com/google/benchmark

+++

**gtest** - unit testing framework.

**gmock** - used to easily write [mock](https://en.wikipedia.org/wiki/Mock_object) C++ classes.

**gbenchmark** - used to benchmark our code.

+++

All tests, mocks and benchmarks are located in  `test` folder.

Build of tests can be enabled or disabled:

```bash
cmake .. -DTESTING=OFF
cmake .. -DBENCHMARKING=ON
cmake .. # -DTESTING=ON by default
```

@[1](neither tests, nor benchmarks are built)
@[2](both tests and benchmarks are built)
@[3](only tests are built)

+++

For every component we write separate interface and implementation. Interface is passed to other components as dependency. It increases testability of our code.

![](http://www.codeguru.com/images/article/15209/Model.jpg)

+++


gmock

```C++
class MockConsensusGate : public ConsensusGate {
 public:
  MOCK_METHOD1(vote, void(model::Block));
};

class Iroha {
 public:
  Iroha(std::shared_ptr<ConsensusGate> c);
}

std::shared_ptr<ConsensusGate> mock =
  std::make_shared<MockConsensusGate>();
Iroha iroha(mock);
```
@[1](ConsensusGate is an interface. MockConsensusGate is mock implementation.)
@[3](this is a special definition, gmock syntax)
@[6-9](class that has dependency on ConsensusGate)
@[11-13](in tests now it is possible to use mock implementation instead of real implementation)

+++

gtest

```C++
TEST(TestSuiteName, TestCaseName) {
  ASSERT_EQ(1, 1);
  ASSERT_TRUE(false) << "false should be true!";
}
```

+++

gbenchmark

```C++
static void howFastIsOptionalCreation(benchmark::State &state) {
  while (state.KeepRunning()) {
    boost::optional<int> a = 5;
  }
}

BENCHMARK(BM_StringCreation);
BENCHMARK_MAIN();
```
