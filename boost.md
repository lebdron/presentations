### boost 1.58+

http://www.boost.org/
+++

**Boost** provides free peer-reviewed portable C++ source libraries.

+++

- multiprecision for `uint256_t`
- filesystem for cross-platform file management
  - system
- optional as replacement for `nonstd::optional`
- variant

+++

```c++
boost::variant<A, B, C, D> v;
v = A();
v = B();
v = C();
v = D();
```

+++

To install all boost libraries locally:

Debian
```bash
$ sudo apt-get install libboost-all-dev
```
OSX
```bash
$ brew install libboost-all-dev
```
