### optional-lite (legacy)

https://github.com/martinmoene/optional-lite/

+++

**optional lite** is a single-file header-only library to represent optional (nullable) objects and pass them by value.

+++

Typical use case - replacement for exceptions:

```C++
nonstd::optional<int> safediv(int a, int b){
  if(b == 0)
    return nonstd::nullopt;
  else
    return a / b;
}
```

+++

**optional** allows to do call chaining:

```C++
nonstd::optional<Object> obj =
  make_object()
  | f2
  | f3
  | f4;
```

Essentially, `obj` will hold `Object` if and only if all transformations `(f2, f3, f4)` returned `Object`, and not `nullopt`.

+++

Implementation of `operator |` ([monadic](https://en.wikipedia.org/wiki/Monad_(functional_programming) bind)
```C++
template <typename T, typename Func>
auto operator | (T t, Func f) -> decltype(f(*t)) {
  if(t) return f(*t);
  else  return t;
}
```
