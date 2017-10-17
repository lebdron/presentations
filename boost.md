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
boost::variant<
    AddPeer,
    TransferAsset,
    ...
  > v;

/* v  can be one of */
v = TransferAsset();
v = AddPeer();

boost::apply_visitor(
  make_visitor(
    [] (AddPeer const& a)      { /* v has AddPeer */      },
    [] (TransferAsset const& a){ /* v has TransferAsset */},
  ),
  v /* apply visitor to variant */
)
```

+++

Recommended approach is to install all boost libraries locally:

Debian
```bash
$ sudo apt-get install libboost-all-dev
```
OSX
```bash
$ brew install boost
```
